<script setup>
const props = defineProps(['campoA', 'campoB', 'editaFiltro', 'valInput1', 'valFiltro', 'valInput2', 'valGetOperator'])
</script>

<template>
    <form class="form-control bg-light">
        <div class="row">
            <div class="col-lg-4 col-sm-6">
                <input @keyup="campoA" class="form-control mt-2" placeholder="Digite um número" type="number">
            </div>
            <div class="col-lg-4 col-sm-6">
                <input @keyup="campoB" class="form-control mt-2" placeholder="Digite um número" type="number">
            </div>
            <div class="col-lg-3">
                <select @change="editaFiltro" class="form-control mt-2 btn btn-primary">
                    <option value="Escolha a operação">Operações :</option>
                    <option value="+">+ Somar</option>
                    <option value="-">- Subtrair</option>
                    <option value="*"> * Multiplicar</option>
                    <option value="/">/ Dividir</option>
                </select>
            </div>
        </div>
        <div class="row">
            <div class="col-lg-8">
                <span placeholder="Resultado" class="form-control mt-2">Resultado: {{ props.valInput1 }} {{ props.valFiltro}}
                    {{ props.valInput2 }} = {{ props.valGetOperator }}</span>
            </div>
            <div class="col-lg-3  mt-2" placeholder="Resultado">
                <button @submit="operator" class="btn btn-danger  form-control">Limpar</button>
            </div>
        </div>
    </form>
</template>

