<script setup>
import { reactive, computed } from 'vue';

const estado = reactive({
  numero1: 0,
  numero2: 0,
  operacao: '+',
});

const calcularResultado = computed(() => {
  switch (estado.operacao) {
    case '+': return estado.numero1 + estado.numero2;
    case '-': return estado.numero1 - estado.numero2;
    case '*': return estado.numero1 * estado.numero2;
    case '/': return estado.numero2 !== 0 ? estado.numero1 / estado.numero2 : 'Erro (divisão por zero)';
    default: return 0;
  }
});
</script>

<template>
  <div class="container">
    <h2>Calculadora Aritmética</h2>
    <input type="number" v-model.number="estado.numero1" placeholder="Digite o primeiro número" class="input">
    <select v-model="estado.operacao" class="select">
      <option value="+">Soma (+)</option>
      <option value="-">Subtração (-)</option>
      <option value="*">Multiplicação (*)</option>
      <option value="/">Divisão (/)</option>
    </select>
    <input type="number" v-model.number="estado.numero2" placeholder="Digite o segundo número" class="input">
    <div class="resultado">Resultado: {{ calcularResultado }}</div>
  </div>
</template>

<style scoped>

.container {
  max-width: 300px;
  margin: auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 10px;
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);
  text-align: center;
  margin-top: 110px;
}

.input, .select {
  width: 100%;
  padding: 8px;
  margin: 10px 0;
  font-size: 16px;
  border: 2px solid black;
  border-radius: 10px;
}

.select {
  border-color: blue;
}

.resultado {
  font-size: 20px;
  font-weight: bold;
  margin-top: 20px;
}
</style>
