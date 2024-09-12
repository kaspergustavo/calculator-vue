<script setup>
import { computed, reactive } from 'vue';

  const estado = reactive({
    numero1: '',
    numero2: '',
    operacao: 'soma',
  });

  const resultado = computed(() => {
    let n1 = parseFloat(estado.numero1);
    let n2 = parseFloat(estado.numero2);

    if (isNaN(n1) || isNaN(n2)) {
      return 'ERROR'
    }

    switch (estado.operacao) {
      case 'soma':
        return n1 + n2;
      case 'subtracao':
        return n1 - n2;
      case 'multiplicacao':
        return n1 * n2;
      case 'divisao':
        return n2 !== 0 ? n1 / n2 : 'ERRO - divisão por zero!';
      default:
        return 0;
    }
  });

  const resultadoClass = computed(() => {
    if (typeof resultado.value === 'string') {
      return 'erro';
    } else if (resultado.value > 0) {
      return 'positivo';
    } else if (resultado.value < 0) {
      return 'negativo';
    } else {
      return 'neutro';
    }
  });

</script>


<template>

  <div class="container mt-5 bg-light rounded-4">
    <div class="row justify-content-center">
      <div class="col-md-9">
        <h1 class="text-center mb-4">Calculadora</h1>
        <div class="form-group mb-3">
          <label class="info mb-1" for="numero1">Primeiro número:</label>
          <input type="number" v-model="estado.numero1" class="form-control" id="numero1" placeholder="Digite aqui o primeiro número">
        </div>
        <div class="form-group mb-3">
          <label class="info mb-1" for="numero2">Segundo número:</label>
          <input type="number" v-model="estado.numero2" class="form-control" id="numero2" placeholder="Digite aqui o segundo número">
        </div>
        <div class="form-group mb-4">
          <label for="operacao" class="info mb-1">Operação</label>
          <select v-model="estado.operacao" class="form-control" id="operacao">
            <option value="soma">Somar (+)</option>
            <option value="subtracao">Subtração (-)</option>
            <option value="multiplicacao">Multiplicação</option>
            <option value="divisao">Divisão</option>
          </select>
        </div>
        <h3 :class="resultadoClass">O resultado do cálculo aritmético foi: {{ resultado }}</h3>
      </div>
    </div>
  </div>

</template>


<style scoped>

  .info {
    color: #007bff;
  }

  h1 {
    color: #007bff
  }

  .positivo {
    color: rgb(1, 110, 1);
  }

  .negativo {
    color: rgb(238, 0, 0);
  }

  .neutro {
    color: #007bff;
  }

  .erro {
    color: rgb(253, 170, 17);
  }

</style>