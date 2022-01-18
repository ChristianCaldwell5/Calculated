
<template>
  <div id="game" class="calculator">
    <h1>CALCULATED</h1>
    <p>Solve the linear equation for X</p>
    <p>Answers should be whole numbers or reduced fractions. No decimals.</p>
    <p>{{ mathProblemDisplay }}</p>
    <input v-model="userAnswer" type="text"><br>
    <button @click="submitAnswer">submit answer</button>
    <button @click="generateRandomMathProblem">generate equation</button>
  </div>
</template>

<script>
// import sounds
import pass from '../assets/sounds/pass.mp3';
import bruh from '../assets/sounds/Bruh.mp3';
import oof from '../assets/sounds/oof.mp3';
import doh from '../assets/sounds/doh.mp3';
import ask from '../assets/sounds/ask.mp3';
import crickets from '../assets/sounds/crickets.mp3';

let failCollection = [bruh, oof, doh, ask, crickets];

export default {
  name: 'Game',
  data: function() {
    return {
      mathProblemDisplay: '',
      linearMathEquation: {
        y: 0,
        m: 0,
        x: 0,
        b: 0
      },
      userAnswer: ''
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
        x: 0,
        b: 0
      }
      for (const c in linearEquation) {
        const constant = Math.floor(Math.random() * 21);
        if (c !== 'x') {
          linearEquation[c] = constant;
        }
      }
      linearEquation.x = this.solveLinearEquation(linearEquation);
      console.log(linearEquation);
      return linearEquation;
    },
    solveLinearEquation(equationObject) {
      const initialResult = (equationObject['y']-equationObject['b'])/equationObject['m'];
      // check if number is not whole to assign fraction value
      if (initialResult % 1 !== 0) {
        // get gcd
        const gcd = this.gcd(Math.abs(equationObject['y']-equationObject['b']), equationObject['m']);
        console.log(gcd);
        const reducedNumerator = (equationObject['y']-equationObject['b'])/gcd;
        const reducedDenominator = equationObject['m']/gcd
        return reducedNumerator + "/" + reducedDenominator;
      } else {
        return initialResult;
      }
    },
    gcd(num1, num2) {
      //if num2 is 0 return num1;
      if(num2 === 0){
          return num1;
      }
      
      //call the same function recursively
      return this.gcd(num2, num1 % num2);
    },
    convertEquationObjectToString(equationObject, type) {
      if (type === 'linear') {
        return equationObject['y'] + ' = ' + equationObject['m'] + 'x + ' + equationObject['b'];
      }
      return '';
    },
    submitAnswer() {
      let audio;
      if (this.linearMathEquation.x.toString() === this.userAnswer) {
        audio = new Audio(pass);
        audio.play();
        this.generateRandomMathProblem();
      } else {
        let randSeed = Math.floor(Math.random() * failCollection.length);
        audio = new Audio(failCollection[randSeed]);
        audio.play();
      }
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
