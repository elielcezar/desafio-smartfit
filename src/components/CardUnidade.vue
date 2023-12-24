<template>
    <div class="unidade" :key="unidade.id">
      <h3>{{ unidade.title }}</h3>
      <p><strong>Está aberta?</strong> {{ unidade.opened }}</p>
      <p><strong>Uso de máscara:</strong> {{ unidade.mask }}</p>
      <p><strong>Horário</strong>: {{ unidade.schedules[0].hour }} </p>
    </div>
</template>

<script>
export default {
  props: ['unidade'],
  name: 'CardUnidade'
}
</script>

<style>

</style>