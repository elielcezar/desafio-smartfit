<template>
  <footer>
    <img src="../assets/images/logo.svg" alt="">
    <p>Todos os direitos reservados - 2020</p>
  </footer>  
</template>

<script>
export default {
  name: 'MainFooter'
}
</script>

<style scoped>

footer {
  width: 100%;
  padding: 50px 0;
  background: var(--dark-grey);
  text-align: center;
  margin-top: 50px;
}

footer img {
  width: 220px;
  height: auto;  
  display: inline-block;  
  margin: 0;
}

footer p{
  color: #fff
}



</style>