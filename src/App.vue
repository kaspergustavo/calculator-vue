<script setup>

</script>

<template>
  <div class="calculator mw-400 m-50 p-20 rounded-">
    <h2>Calculadora do Gustavo</h2>
    <input type="number" v-model.number="numero1" placeholder="Digite o primeiro número">
    <input type="number" v-model.number="numero2" placeholder="Digite o segundo número">
    <select v-model="operacao">
      <option value="soma">Somar (+)</option>
      <option value="subtracao">Subtrair (-)</option>
      <option value="multiplicacao">Multiplicar (x)</option>
      <option value="divisao">Dividir (÷)</option>
    </select>
    <h3>Resultado: {{ resultado }}</h3>
  </div>
</template>

<style scoped>

</style>
