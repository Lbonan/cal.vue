<script setup>
import { reactive } from "vue";

const estado = reactive({
  resultado: 0,
  primeiroNumero: "",
  segundoNumero: "",
  operacao: "soma",
});

const calculaResultado = () => {
  const num1 = parseFloat(estado.primeiroNumero);
  const num2 = parseFloat(estado.segundoNumero);

  const { operacao } = estado;

  switch (operacao) {
    case "soma":
      return (estado.resultado = num1 + num2);
    case "subtracao":
      return (estado.resultado = num1 - num2);
    case "multiplicacao":
      return (estado.resultado = num1 * num2);
    case "divisao":
      return (estado.resultado = estado.resultado = num2 !== 0 ? num1 / num2 : "Erro: divisão por zero");
    default:
      estado.resultado = "Operação inválida";
  }
};
</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 bg-dark rounded-3">
      <h1>Calculadora aritmética</h1>
    </header>
    <form>
      <div class="row">
        <div class="col-3">
          <input type="number" v-model="estado.primeiroNumero" placeholder="Digite o número" @input="calculaResultado" />
        </div>
        <div class="col">
          <input type="number" v-model="estado.segundoNumero" placeholder="Digite o número" @input="calculaResultado" />
        </div>
        <div class="col-3">
          <select class="form-control" v-model="estado.operacao" @change="calculaResultado">
            <option value="soma">Soma</option>
            <option value="subtracao">Subtração</option>
            <option value="multiplicacao">Multiplicação</option>
            <option value="divisao">Divisão</option>
          </select>
        </div>
      </div>
    </form>
    <p>Resultado:{{ estado.resultado }}</p>
  </div>
</template>

<style scoped>
h1 {
  color: #fff;
}
</style>
