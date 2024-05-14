<script setup>
import { reactive } from 'vue';
import Formulario from './components/Formulario.vue';

const estado = reactive({
  numeroA: 0,
  numeroB: 0,
  operacoes: {
      adicao: (a, b) => a + b,
      subtracao: (a, b) => a - b,
      multiplicacao: (a, b) => a * b,
      divisao: (a, b) => b !== 0 ? a / b : 'Invalido'
  },
  resultado: 0,
})

const calculo = () => {
  const { numeroA, numeroB, operacaoEscolhida} = estado;
  estado.resultado = estado.operacoes[operacaoEscolhida](parseInt(numeroA), parseInt(numeroB));
}
</script>

<template>
  <div class="container">
    <Formulario :numero-A="evento => estado.numeroA = evento.target.value" :numero-B="evento => estado.numeroB = evento.target.value" :operacao="estado.operacaoEscolhida" :calculo="calculo" :result="estado.resultado"/>
  </div>
</template>

<style scoped>
</style>
