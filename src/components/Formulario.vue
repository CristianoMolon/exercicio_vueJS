<script setup>
import { reactive } from 'vue';

const estado = reactive({
    numeroA: 0,
    numeroB: 0,
    operacoes: {
        adicao: (a, b) => a + b,
        subtracao: (a, b) => a - b,
        multiplicacao: (a, b) => a * b,
        divisao: (a, b) => (b !== 0 ? a / b : 'Invalido'),
    },
    resultado: 0,
})

const calculo = () => {
    const { numeroA, numeroB, operacaoEscolhida } = estado;
    estado.resultado = estado.operacoes[operacaoEscolhida](parseInt(numeroA), parseInt(numeroB));
}
</script>

<template>
    <form class="form-horizontal text-center pt-4">
        <div class="mb-3 form-group">
            <h1>Calculadora Aritmetica</h1>
            <label for="A" class="control-label">Primeiro numero</label>
            <input v-model="estado.numeroA" @input="calculo" class="form-control d-flex m-auto mb-3" type="number"
                id="A">
            <label for="B" class="control-label">Segundo numero</label>
            <input v-model="estado.numeroB" @input="calculo" class="form-control d-flex m-auto mb-3" type="number"
                id="B">
        </div>
        <div>
            <select v-model="estado.operacaoEscolhida" @change="calculo" class="form-control d-inline">
                <option value="adicao">Adição</option>
                <option value="subtracao">subtraçao</option>
                <option value="multiplicacao">Multiplicação</option>
                <option value="divisao">Divisão</option>
            </select>
        </div>
        <p class="pt-4">
            O resultado foi {{ estado.resultado }}.
        </p>
    </form>
</template>

<style scoped>
input,
select {
    max-width: 80px;
    width: 100%;
}
</style>