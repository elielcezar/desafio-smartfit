<template>
  <div id="legendas">
    <div class="legenda mascara">
      <h4>Máscara</h4>
      <div class="item obrigatorio"><p>Obrigatório</p></div>
      <div class="item recomendado"><p>Recomendado</p></div>
    </div>
    <div class="legenda toalha">
      <h4>Toalha</h4>
      <div class="item obrigatorio"><p>Obrigatório</p></div>
      <div class="item recomendado"><p>Recomendado</p></div>
    </div>
    <div class="legenda bebedouro">
      <h4>Bebedouro</h4>
      <div class="item parcial"><p>Parcial</p></div>
      <div class="item proibido"><p>Proibido</p></div>
    </div>
    <div class="legenda vestiarios">
      <h4>Vestiários</h4>
      <div class="item liberado"><p>Liberado</p></div>
      <div class="item parcial"><p>Parcial</p></div>
      <div class="item fechado"><p>Fechado</p></div>
    </div>
  </div>  
</template>

<script>
export default {
  name: 'Legendas'
}
</script>

<style scoped>

#legendas{
  padding: 20px 10px; 
  background: #f5f5f5;
  display: flex;
  flex-wrap: wrap;
  margin: 25px 0;
}
#legendas .legenda{   
  width: 25%;   
  text-align: center;
  display: flex;  
  flex-wrap: wrap;
}

#legendas .legenda.bebedouro{
  width: 21%;
  margin: 0 2%;
}

#legendas .legenda h4{
  width: 100%;
  margin: 0 0 10px 0;
  font-family: 'Gotham Bold';
}
#legendas .legenda .item{
    width: 50%;      
    padding-top: 75px;
    background-repeat: no-repeat;
    background-position: top center;
    background-size: 65px;
  }
  #legendas .legenda .item p{
    margin: 0
  }
  #legendas .legenda.mascara .item.obrigatorio{
    background-image: url(../assets/images/required-mask.png);
  }
  #legendas .legenda.mascara .item.recomendado{
    background-image: url(../assets/images/recommended-mask.png);
  }

  #legendas .legenda.toalha .item.obrigatorio{
    background-image: url(../assets/images/required-towel.png);
  }
  #legendas .legenda.toalha .item.recomendado{
    background-image: url(../assets/images/recommended-towel.png);
  }

  #legendas .legenda.bebedouro .item.parcial{
    background-image: url(../assets/images/partial-fountain.png);
  }
  #legendas .legenda.bebedouro .item.proibido{
    background-image: url(../assets/images/forbidden-fountain.png);
  }

  #legendas .legenda.vestiarios .item{
    width: 33.33%;
    background-size: 90% auto;    
  }
  #legendas .legenda.vestiarios .item.liberado{
    background-image: url(../assets/images/required-lockerroom.png);
  }
  #legendas .legenda.vestiarios .item.parcial{
    background-image: url(../assets/images/partial-lockerroom.png);
  }
  #legendas .legenda.vestiarios .item.fechado{
    background-image: url(../assets/images/forbidden-lockerroom.png);
  }



  @media(max-width:768px){

  }
/*@media(orientation:portrait){  
  #legendas{
    flex-direction: column
  }
  #legendas .legenda{
    width: 100%
  }
}
@media(orientation:landscape){
  #legendas .legenda{
    flex: 1;
  }  
  #legendas .legenda .item{
    width: 50%;
  }
  #legendas .legenda.vestiarios .item{
    width: 33.33%;
  }
}*/

</style>