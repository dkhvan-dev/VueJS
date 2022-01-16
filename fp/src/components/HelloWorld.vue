<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    {{ message }}

  <input type="text" v-model.number="operand1" />
  <input type="text" v-model.number="operand2" />

  = {{ result }}

  <button @click="sum(operand1, operand2)">+</button>
  <button @click="difference(operand1, operand2)">-</button>
  <button @click="divide(operand1, operand2)">/</button>
  <button @click="multiply(operand1, operand2)">*</button>
  <button @click="intDivide(operand1, operand2)">intDivide</button>
  <button @click="exponentiation(operand1, operand2)">x^y</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  
  data() {
    return {
      disabled: true,
      message: 'Hello Vue',
      operand1: 0,
      operand2: 0,
      result: 0 as number
    }
  },

  methods: {
    sum(op1:number, op2:number) {
      this.result = op1 + op2;
    },

    difference(op1:number, op2:number) {
      this.result = op1 - op2;
    },

    divide(op1:number, op2:number) {
      this.result = op1 / op2;
    },

    multiply(op1:number, op2:number) {
      this.result = op1 * op2;
    },

    intDivide(op1:number, op2:number) {
      let divideValue = (op1 / op2);
      this.result = Math.round(divideValue);
    },

    exponentiation(op1:number, op2:number) {
      let exp = 1;
      while (op2 > 0) {
        exp *= op1;
        op2--;
      }

      this.result = exp;
    }
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
