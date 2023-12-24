<template>
  <div class="home">
    <MainHeader/>
    <ListaHorarios/>        
    <MainFooter/>
  </div>
</template>

<script>

import MainHeader from '@/components/MainHeader.vue';
import ListaHorarios from '@/components/ListaHorarios.vue';
import MainFooter from '@/components/MainFooter.vue';


export default {
  name: 'HomeView',
  components: {
    MainHeader,
    ListaHorarios,    
    MainFooter
  }
}
</script>
