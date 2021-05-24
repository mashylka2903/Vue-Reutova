<template>
  <div class="hello">
    
    <input v-model.number="operand1" ref="op1"/>
    <input v-model.number="operand2" ref="op2"/>
    = {{ result }}
    <div>
      <button v-for="op in operations" 
      v-bind:key="op"
      @click="calculate(op)">
      {{ op }}
      </button>
    </div>
    <input type="checkbox" id="keyboard" value="Keyboard" v-model="showKeyboard">
    <label for="keyboard">Show keyboard</label>
  
    <div class="numbers" v-if="showKeyboard">
      
      <button v-for="(btn, item) in collection" 
      :key="item"
      @click="inputNum(btn)"> 
      {{ btn }}    
      </button>
      <button>            
       backspace
      </button>
    <br>        
        <input type="radio" id="one" value="1" v-model="chosen"/>
        <label for="one">Operand 1</label>
        <input type="radio" id="two" value="2" v-model="chosen"/>
        <label for="two">Operand 2</label>
    </div>
  </div>
</template>

<script>

export default {
  
  data: () => ({ 
    operand1: 0,
    operand2: 0,
    result: 0, 
    collection: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
    operations: ['+', '-', '/', '*', '**', '%'],
    showKeyboard: false,
    chosen: ''
  }),
  props: {
    
  },
  methods: {   
  
  inputNum(i) {
    const { chosen } = this
    const input = chosen === '1' ? 'operand1' : 'operand2'
    this[input] = +(this[input] += String(i))
  },
  
  calculate (operation) {
    const operand1 = this.operand1
    const operand2 = this.operand2
  switch(operation) {
    case '+' :
      this.result = operand1 + operand2;
      break;
    case '-' :
      this.result = operand1 - operand2;
      break;  
    case '/' :
      this.result = operand1 / operand2;
      break; 
    case '*' :
      this.result = operand1 * operand2;
      break; 
      case '**' :
      this.result = operand1 ** operand2;
      break; 
      case '%' :
      this.result = operand1 % operand2;
      break; 
      }
   } 
    
  },
  computed: {

  },
  watch: {
    
  },
  created () {},
  mounted () {},
  updated () {},
  beforeDestroy () {}
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
.textarea {
  padding: 20px;
  border: 1px soled red;
}
</style>
