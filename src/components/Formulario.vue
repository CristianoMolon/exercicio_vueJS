<script setup>
    const props = defineProps(['numeroA', 'numeroB', 'calculo', 'operacao', 'result']);
</script>

<template>
    <form class="form-horizontal text-center pt-4">
        <div class="mb-3 form-group">
            <h1>Calculadora Aritmetica</h1>
            <label for="A" class="control-label">Primeiro numero</label>
            <input @change="props.numeroA" @input="props.calculo" class="form-control d-flex m-auto mb-3" type="number" id="A">
            <label for="B" class="control-label">Segundo numero</label>
            <input @change="props.numeroB" @input="props.calculo" class="form-control d-flex m-auto mb-3" type="number" id="B">
        </div>
        <div>
            <select v-model="props.operacao" @change="props.calculo" class="form-control d-inline">
                <option value="adicao">Adição</option>
                <option value="subtracao">subtraçao</option>
                <option value="multiplicacao">Multiplicação</option>
                <option value="divisao">Divisão</option>
            </select>
        </div>
        <p class="pt-4">
            O resultado foi {{ props.result }}.
        </p>
    </form>
</template>

<style>
input, select {
    max-width: 80px;
    width: 100%;
}
</style>