<template>
  <div id="app">
    <h1>Calculadora Aritmética</h1>
    <div>
      <input type="number" v-model.number="num1" placeholder="Número 1" />
      <select v-model="operacao">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
      </select>
      <input type="number" v-model.number="num2" placeholder="Número 2" />
    </div>
    <div v-if="resultado !== null">
      <h2>Resultado: {{ resultado }}</h2>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      num1: 0,
      num2: 0,
      operacao: '+',
      resultado: null
    };
  },
  watch: {
    num1: 'calcularResultado',
    num2: 'calcularResultado',
    operacao: 'calcularResultado'
  },
  methods: {
    calcularResultado() {
      if (this.operacao === '+') {
        this.resultado = this.num1 + this.num2;
      } else if (this.operacao === '-') {
        this.resultado = this.num1 - this.num2;
      } else if (this.operacao === '*') {
        this.resultado = this.num1 * this.num2;
      } else if (this.operacao === '/') {
        if (this.num2 === 0) {
          this.resultado = 'Erro: Divisão por zero';
        } else {
          this.resultado = this.num1 / this.num2;
        }
      }
    }
  }
};
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

input {
  margin: 10px;
  padding: 5px;
  font-size: 16px;
}

select {
  margin: 10px;
  padding: 5px;
  font-size: 16px;
}

h1 {
  font-size: 2em;
}

h2 {
  font-size: 1.5em;
}
</style>
