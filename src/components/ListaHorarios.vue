<template>

  <div class="container">
    <form @submit.prevent="handleForm">
    <h4>Horário 65465</h4>
    <h3>Em qual período quer treinar?</h3>
    <div class="form-item">
      <input type="radio" name="periodo" v-model="periodo" id="manha" value="manha">
      <label for="manha">Manhã <span>06:00 às 12:00</span></label>
    </div>
    <div class="form-item">
      <input type="radio" name="periodo" v-model="periodo" id="tarde" value="tarde">
      <label for="tarde">Tarde <span>12:01 às 18:00</span></label>
    </div>
    <div class="form-item">
      <input type="radio" name="periodo" v-model="periodo" id="noite" value="noite">
      <label for="noite">Noite <span>18:01 às 23:00</span></label>
    </div>
    <div class="form-item opcoes">
      <div class="exibir">
        <input type="checkbox" name="exibir_unidades" value="sim" id="exibir_unidades" v-model="exibir_unidades">
        <label for="exibir_unidades">Exibir unidades fechadas</label>
      </div>
      <div class="resultados">
        <p>Resultados enconrtados: <strong>{{ totalResultados }}</strong></p>
      </div>
    </div>
    <div class="form-item buttons">
      <button class="enviar">Encontrar Unidade</button>
      <button class="limpar" type="reset" @click="clearData">Limpar</button>
    </div>
  </form>

  <Legendas/>
    
  <div v-if="filtroUnidades">
    <div id="unidades">
      <div v-for="unidade in filtroUnidades">
        <CardUnidade :unidade="unidade" />
      </div>
    </div>  
  </div> 

  </div>
</template>

<script>

import CardUnidade from './CardUnidade.vue'
import Legendas from './Legendas.vue'

export default {
  name: 'ListaHorarios',
  components: {CardUnidade, Legendas},
  data(){
    return{
      periodo: '',
      exibir_unidades: '', 
      unidades: [],
      filtroUnidades: '',
      totalResultados: '0'
    }
  },
  methods:{
    clearData(){
      this.filtroUnidades = '',
      this.totalResultados = '0'
    },
    handleForm(){  

        // monta o array de unidades abertas pela manha
        const unidadesManha = []
        this.unidades.forEach(function(unidade){          
          if(unidade.schedules){     
              const firstTwoChars = parseInt(unidade.schedules[0].hour.slice(0, 2));   
              if(firstTwoChars < 12){                 
                unidadesManha.push(unidade);                
              }  
          }else{
            unidade.schedules = null
          }
        });

        // monta o array de unidades abertas pela tarde
        const unidadesTarde = []
        this.unidades.forEach(function(unidade){          
          if(unidade.schedules){                   
              const lastThreeChars = parseInt(unidade.schedules[0].hour.slice(-3).slice('h'));                            
              if(lastThreeChars > 12){
                unidadesTarde.push(unidade)                
              }    
          }else{
            unidade.schedules = null
          }
        });

        // monta o array de unidades abertas pela noite
        const unidadesNoite = []
        this.unidades.forEach(function(unidade){          
          if(unidade.schedules){                   
              const lastThreeChars = parseInt(unidade.schedules[0].hour.slice(-3).slice('h'));                            
              if(lastThreeChars > 18){                
                unidadesNoite.push(unidade)
              }  
          }else{
            unidade.schedules = null
          }
        });

        if(this.periodo == 'manha'){                           
          this.filtroUnidades = unidadesManha.filter(unidade => (unidade.opened == true));
        }else if((this.periodo == 'manha') && (this.exibir_unidades)){
          this.filtroUnidades = unidadesManha
        }else if(this.periodo == 'tarde'){          
          this.filtroUnidades = unidadesTarde.filter(unidade => (unidade.opened == true));
        }else if((this.periodo == 'tarde') && (this.exibir_unidades)){
          this.filtroUnidades = unidadesManha
        }else if(this.periodo == 'noite'){          
          this.filtroUnidades = unidadesNoite.filter(unidade => (unidade.opened == true));
        }else if((this.periodo == 'noite') && (this.exibir_unidades)){
          this.filtroUnidades = unidadesNoite
        }
        
        // exibe o total de resultados obtidos
        this.totalResultados = this.filtroUnidades.length; 
    }
  },
  mounted() {    
    fetch('https://test-frontend-developer.s3.amazonaws.com/data/locations.json')
    .then(res => res.json())
    .then(res => { this.unidades = res.locations })
    .catch(error => console.log(error.message));     
  }
}
</script>

<style scoped>
  form{
    width: 100%;
    padding: 25px;
    border: 4px solid var(--lighter-grey);
    border-radius: 9px;
  }

  form h4{
    font-size: .85rem;
    color: var(--light-grey);
    font-family: 'Gotham Light';
  }

  form h3{
    font-size: 1.25rem;
    color: var(--light-grey);
    font-family: 'Gotham Light';
    padding: 15px 0;
    margin: 0;
    border-bottom: 2px solid var(--lighter-grey);
  }

  .form-item{
    width: 100%;
    padding: 15px 0;
    margin: 10px 0;
    border-bottom: 2px solid var(--lighter-grey);
    color: var(--light-grey);
    display: flex;    
  }
  .form-item label{
    display: flex;
    justify-content: space-between;
    flex-grow: 1;
    margin-left: 5px;    
  }

  .form-item.opcoes{
    display: flex;
    justify-content: space-between;
  }
  .form-item .exibir{
    display: flex;    
    align-items: center;
  }
  .form-item .resultados strong{
    font-size: 1.3rem;
    font-family: 'Gotham Bold'
  }
  .form-item.buttons{
    display: flex;
    justify-content: center;
  }

  button{
    display: inline-block;
    padding: 15px;
    border: none;
    border: 2px solid var(--lighter-grey);
    color: #000;
    text-transform: uppercase;
    font-family: 'Gotham Bold';
    font-size: .9rem;
    letter-spacing: 1px;
    background: #fff;
    min-width: 30%;
    margin: 0 5%;
    transition: all .3s;
  }
  button.enviar{
    background: var(--yellow);
    border: 2px solid var(--yellow)
  }
  button:hover{
    background: var(--dark-grey);
    color: #fff;
    border: 2px solid var(--dark-grey)
  }

#unidades{
  display: flex;
  flex-wrap: wrap;
}
#unidades > div{
  width: 100%;
  max-width: 33.33%;
  padding: 1.5%;  
}
</style>