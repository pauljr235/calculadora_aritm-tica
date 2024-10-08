<script>
export default {
  data() {
    return {
      numero1: 0,
      numero2: 0,
      operacao: "soma",
    };
  },
  computed: {
    resultado() {
      switch (this.operacao) {
        case "soma":
          return this.numero1 + this.numero2;
        case "subtracao":
          return this.numero1 - this.numero2;
        case "multiplicacao":
          return this.numero1 * this.numero2;
        case "divisao":
          return this.numero2 !== 0 ? (this.numero1 / this.numero2).toFixed(2) : "Erro: Divisão por zero";
        default:
          return 0;
      }
    },
  },
};
</script>


<template>
  <div class="container mt-5">
    <div class="card p-4">
      <h2 class="text-center mb-4">Calculadora Aritmética</h2>
      <div class="form-group">
        <label for="numero1">Número 1:</label>
        <input v-model.number="numero1" type="number" class="form-control" placeholder="Insira o primeiro número" />
      </div>

      <div class="form-group">
        <label for="numero2">Número 2:</label>
        <input v-model.number="numero2" type="number" class="form-control" placeholder="Insira o segundo número" />
      </div>
      
      <div class="form-group">
        <label for="operacao">Operação:</label>
        <select v-model="operacao" class="form-control">
          <option value="soma">Somar</option>
          <option value="subtracao">Subtrair</option>
          <option value="multiplicacao">Multiplicar</option>
          <option value="divisao">Dividir</option>
        </select>
      </div>
      <h4 class="text-center mt-4">Resultado: {{ resultado }}</h4>
    </div>
  </div>
</template>



<style scoped>
.container {
  max-width: 500px;
}

h2, h4 {
  color: #333;
}
</style>
