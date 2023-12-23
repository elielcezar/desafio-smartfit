<template>
  <div class="home">
    <MainHeader/>
    <FormHorarios/>        
    <MainFooter/>
  </div>
</template>

<script>

import MainHeader from '@/components/MainHeader.vue';
import FormHorarios from '@/components/FormHorarios.vue';
//import Legendas from '@/components/Legendas.vue';
//import ListaResultados from '@/components/ListaResultados.vue';
import MainFooter from '@/components/MainFooter.vue';


export default {
  name: 'HomeView',
  components: {
    MainHeader,
    FormHorarios,
    //Legendas,
    //ListaResultados,
    MainFooter
  }
}
</script>
