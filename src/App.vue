<script>
  import { reactive } from 'vue';

  const estado = reactive({
    valor1: 0,
    valor2: 0,
    operacao: ''
  });

  const resultado = () => {
    const{ operacao, valor1, valor2 } = estado;

    switch (operacao) {
      case 'soma':
        return valor1 + valor2;
      case 'subtracao':
        return valor1 - valor2;
      case 'multiplicacao':
        return valor1 * valor2;
      case 'divisao':
        return valor2 !== 0 ? valor1 / valor2 : 'Erro: Divisão por zero';
      default:
        return 'Operação inválida'
    }
  };
  export default {
    setup() {
      return {
        estado,
        resultado
      };
    }
  }
</script>

<template>
  <div class="container mt-5 bg-light rounded-3">
    <h1>Calculadora Aritmética</h1>
    <div>
      <input type="number" v-model.number="estado.valor1" placeholder="Número 1" />
      <select v-model="estado.operacao">
        <option value="soma">+</option>
        <option value="subtracao">-</option>
        <option value="multiplicacao">*</option>
        <option value="divisao">/</option>
      </select>
      <input type="number" v-model.number="estado.valor2" placeholder="Número 2" />
    </div>
    <h2>Resultado: {{ resultado() }}</h2>
  </div>
</template>

<style scoped>

  .container {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    text-align: center;
    
  }
  input, select {
    margin: 10px;
  }

</style>
