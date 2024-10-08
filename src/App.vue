<script>
import { reactive, watch } from 'vue';

const valor = reactive({
  numero1: 0,
  numero2: 0,
  operacao: "soma",
  resultado: 0,
});

// Função para realizar o cálculo com base na operação selecionada
function calcular() {
  if (valor.operacao === "soma") {
    valor.resultado = valor.numero1 + valor.numero2;
  } else if (valor.operacao === "subtracao") {
    valor.resultado = valor.numero1 - valor.numero2;
  } else if (valor.operacao === "multiplicacao") {
    valor.resultado = valor.numero1 * valor.numero2;
  } else if (valor.operacao === "divisao") {
    valor.resultado = valor.numero2 !== 0 ? valor.numero1 / valor.numero2 : "Erro: Divisão por zero"; //'Divisão por zero não é permitida';
  }
}

// Criar um watcher para observar mudanças e calcular automaticamente
watch([() => valor.numero1, () => valor.numero2, () => valor.operacao], calcular);

export default {
  setup() {
    return { valor }; // Retorna os dados reativos para o template
  }
};
</script>

<template>
  <div class="container mt-4">
    <header>
      <h1>Calculadora Aritmética</h1>
    </header>

    <form>
      <div class="row">
        <!-- Campos de input para os números -->
        <div class="col-3">
          <input
            class="form-control mb-2"
            v-model.number="valor.numero1"
            type="number"
            placeholder="Digite o primeiro número"
          />
          <input
            class="form-control mb-2"
            v-model.number="valor.numero2"
            type="number"
            placeholder="Digite o segundo número"
          />
        </div>

        <!-- Seletor de operações -->
        <div class="col-2">
          <select v-model="valor.operacao" class="form-control">
            <option value="soma">Somar</option>
            <option value="subtracao">Subtrair</option>
            <option value="multiplicacao">Multiplicar</option>
            <option value="divisao">Dividir</option>
          </select>
        </div>

        <!-- Exibição do resultado -->
        <div class="col-12">
          <h4 class="text-center mt-4">Resultado: {{ valor.resultado }}</h4>
        </div>
      </div>
    </form>
  </div>
</template>

<style scoped>
.container {
  max-width: 600px;
}
h1 {
  text-align: center;
  margin-bottom: 20px;
}
</style>
