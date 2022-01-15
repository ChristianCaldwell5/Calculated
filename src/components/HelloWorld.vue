
<template>
  <div id="calculated" class="calculator">
    <h1>CALCULATED</h1>
    <p>{{ mathProblemDisplay }}</p>
    <button @click="generateRandomMathProblem">Generate Number</button>
  </div>
</template>

<script>
export default {
  name: 'Calculator',
  data: function() {
    return {
      mathProblemDisplay: '',
      linearMathEquation: {
        y: 0,
        m: 0,
        b: 0
      }
    }
  },
  methods: {
    generateRandomMathProblem() {
      this.linearMathEquation = this.generateLinearEquation()
      this.mathProblemDisplay = this.convertEquationObjectToString(this.linearMathEquation, 'linear');
    },
    generateLinearEquation() {
      let linearEquation = {
        y: 0,
        m: 0,
        b: 0
      }
      for (const c in linearEquation) {
        const constant = Math.floor(Math.random() * 51);
        linearEquation[c] = constant;
      }
      return linearEquation;
    },
    convertEquationObjectToString(equationObject, type) {
      if (type === 'linear') {
        return equationObject['y'] + ' = ' + equationObject['m'] + 'x + ' + equationObject['b'];
      }
      return '';
    }
  },
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  color: gray;
  font-size: 48px;
  text-align: center;
}
</style>
