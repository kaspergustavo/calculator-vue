<script setup>
import { computed, reactive } from 'vue';

  const estado = reactive({
    numero1: 0,
    numero2: 0,
    operacao: 'soma',
  });

  const resultado = computed(() => {
    let n1 = parseFloat(estado.numero1);
    let n2 = parseFloat(estado.numero2);

    switch (estado.operacao) {
      case 'soma':
        return n1 + n2;
      case 'subtracao':
        return n1 - n2;
      case 'multiplicacao':
        return n1 * n2;
      case 'divisao':
        return n2 !== 0 ? n1 / n2 : 'ERROR: divisão por zero!';
      default:
        return 0;
    }
  });
</script>

<template>
  <div class="container mt-5">
    <div class="row justify-content-center">
      <div class="col-md-6">
        <h1 class="text-center mb-4">Calculadora do Gustavo</h1>
        <div class="form-group mb-3">
          <input type="number" v-model="estado.numero1" class="form-control" id="numero1"
            placeholder="Digite o primeiro número">
        </div>
        <div class="form-group mb-3">
          <input type="number" v-model="estado.numero2" class="form-control" id="numero2"
            placeholder="Digite o segundo número">
        </div>
        <div class="form-group mb-4">
          <label for="operacao" class="operador mb-1">Operação</label>
          <select v-model="estado.operacao" class="form-control" id="operacao">
            <option value="soma">Somar (+)</option>
            <option value="subtracao">Subtração (-)</option>
            <option value="multiplicacao">Multiplicação</option>
            <option value="divisao">Divisão</option>
          </select>
        </div>
        <h3>O resultado do calculo aritmético foi: {{ resultado }}</h3>
      </div>
    </div>
  </div>
</template>

<style scoped>
  .operador {
    color: #007bff;
  }

  h1 {
    color: #007bff
  }

</style>