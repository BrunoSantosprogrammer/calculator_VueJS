<script setup>
import { reactive } from 'vue';

const operator = reactive({
  filtro: '( )',
  input1: '_',
  input2:'_',
})

function soma() {
  return parseInt(operator.input1) + parseInt(operator.input2) ;
}
function sub() {
  return operator.input1 - operator.input2;
}
function mult() {
  return operator.input1 * operator.input2;
}
function div() {
  return operator.input1 / operator.input2;
}

const getOperator = () => {
  const {filtro} = operator;
  switch (filtro) {
    case "+":
      return soma();
    case "-":
      return sub();
    case "*":
      return mult();
    case "/":
      return div();
  } 
}


function campoA(evento) {
  operator.input1 = evento.target.value;
}
function campoB(evento) {
  operator.input2 = evento.target.value;
}



</script>

<template>
  <div class="container text-center bg-secondary">
    <header class="p-4 mt-4">
      <h1>Calculator VueJS</h1>
    </header>
    <form class="form-control bg-light">
      <div class="row">
        <div class="col-lg-4 col-sm-6">
          <input @keyup="campoA" id="campo-A" class="form-control mt-2" placeholder="Digite um número" type="number">
        </div>
        <div class="col-lg-4 col-sm-6">
          <input @keyup="campoB" id="campo-B" class="form-control mt-2" placeholder="Digite um número" type="number">
        </div>
        <div class="col-lg-3">
          <select @change="evento => operator.filtro = evento.target.value" class="form-control mt-2 btn btn-primary">
            <option  value="Escolha a operação">Operações :</option>
            <option  value="+">+ Somar</option>
            <option value="-">- Subtrair</option>
            <option value="*"> * Multiplicar</option>
            <option value="/">/ Dividir</option>
          </select>
        </div>
      </div>
      <div class="row">
        <div class="col-lg-8">
          <span placeholder="Resultado" class="form-control mt-2">Resultado: {{ operator.input1 }} {{ operator.filtro }} {{ operator.input2 }} = {{getOperator()}}</span>
        </div>
        <div class="col-lg-3  mt-2" placeholder="Resultado">
          <button @submit="operator" class="btn btn-danger  form-control">Limpar</button>
        </div>
      </div>
    </form>

  </div>
</template>

<style scoped>
.container {
  max-width: 760px;
  padding-bottom: 50px;
}
</style>
