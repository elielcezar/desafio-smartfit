<template>
  <header>
    <h1>Smart Fit</h1>
  </header>
  <div class="hero">
    <div class="container">
      <h2>Reabertura Smart Fit</h2>
      <p>O horário de funcionamento das nossas unidades está seguindo os decretos de cada município. Por isso, confira aqiu se a sua unidade está aberta e as medidas de segurança que estamos seguindo.</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MainHeader'
}
</script>

<style scoped>

header {
  width: 100%;
  padding: 15px 0;
  background: var(--dark-grey);
  text-align: center;
  margin-bottom: 50px;
}

header h1 {
  width: 220px;
  height: 100px;
  background: transparent url(../assets/images/logo.svg) center no-repeat;
  background-size: 100% auto;
  display: inline-block;
  text-indent: -5000em;
  margin: 0;
}

.hero {
  padding: 25px 0;
}

.hero h2 {
  text-transform: uppercase;
  font-size: 2.5rem;
  font-family: 'Gotham Bold';
  max-width: 300px;  
  position: relative;
  margin: 0 0 25px 0;
  padding-bottom: 25px;
}

.hero h2::after{
  content: '';
  display: block;
  width: 100px;
  height: 10px;
  background: var(--dark-grey);
  position: absolute;
  left: 0;
  bottom: 0;
}


</style>