<template>  
    <div class="unidade" :key="unidade.id">
      <h4 v-if="unidade.opened">Aberto</h4>
      <h4 v-else>Fechado</h4>

      <h3>{{ unidade.title }}</h3>            
      <div class="legendas">    

        <p class="mascara" 
        :class="{
          obrigatorio: unidade.mask == 'required', 
          recomendado: unidade.mask == 'recommended'}">Uso de máscara</p>
        
        <p class="toalha" 
        :class="{
          obrigatorio: unidade.towel == 'required', 
          recomendado: unidade.towel == 'recommended'}">Uso de toalha</p>

        <p class="bebedouro" 
        :class="{
          parcial: unidade.fountain == 'partial', 
          proibido: unidade.fountain == 'not_allowed'}">Uso de bebedouro</p>
 
        <p class="vestiario" 
        :class="{
          permitido: unidade.locker_room == 'allowed', 
          parcial: unidade.locker_room == 'partial', 
          proibido: unidade.locker_room == 'closed'}">Uso de vestiário</p>
        
      </div>
      <div class="horarios">
        <p><strong>Seg. à Sex.</strong> {{ unidade.schedules[0].hour }} </p>
        <p><strong>Sáb.</strong> {{ unidade.schedules[1].hour }} </p>
        <p><strong>Dom.</strong> {{ unidade.schedules[2].hour }} </p>
      </div>
    </div>
  
</template>

<script>
export default {
  props: ['unidade'],
  name: 'CardUnidade'
}
</script>

<style scoped>
.unidade{
  padding: 10px;
  border-radius: 10px;
  background: #f5f5f5;
  box-shadow: 0 0 5px rgba(0,0,0,.5);
  width: 100%;  
}

.unidade .legendas{
  display: flex;
}
.unidade .legendas p{  
  display: inline-block;
  width: 25%;
  padding-top: 60px;
  background-repeat: no-repeat;
  background-position: top center;
  background-size: 90%;
  text-indent: -5000em;
}

.unidade .legendas p.mascara.obrigatorio{background-image: url(../assets/images/required-mask.png);}
.unidade .legendas p.mascara.recomendado{background-image: url(../assets/images/recommended-mask.png);}
.unidade .legendas p.toalha.obrigatorio{background-image: url(../assets/images/required-towel.png);}
.unidade .legendas p.toalha.obrigatorio{background-image: url(../assets/images/recommended-towel.png);}
.unidade .legendas p.bebedouro.parcial{background-image: url(../assets/images/partial-fountain.png);}
.unidade .legendas p.bebedouro.proibido{background-image: url(../assets/images/forbidden-fountain.png);}
.unidade .legendas p.vestiario.permitido{background-image: url(../assets/images/required-lockerroom.png);}
.unidade .legendas p.vestiario.parcial{background-image: url(../assets/images/partial-lockerroom.png);}
.unidade .legendas p.vestiario.proibido{background-image: url(../assets/images/forbidden-lockerroom.png);}

</style>