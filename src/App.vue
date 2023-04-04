<script setup>
import { reactive } from 'vue';
import FileHeader from './components/FileHeader.vue';
import FileForm from './components/FileForm.vue';

const operator = reactive({
  filtro: '(Op)',
  input1: '_',
  input2: '_',
})

function soma() {
  return parseInt(operator.input1) + parseInt(operator.input2);
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
  const { filtro } = operator;
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
    <FileHeader />
      <FileForm :campo-a="campoA" :campo-b="campoB" 
        :edita-filtro="evento => operator.filtro = evento.target.value"
        :val-filtro=" operator.filtro" 
        :val-input1="operator.input1" 
        :val-input2="operator.input2"
        :val-get-operator="getOperator()" />
  </div>
</template>

<style scoped>
.container {
  max-width: 760px;
  width: 100%;
  padding-bottom: 50px;
}
</style>
