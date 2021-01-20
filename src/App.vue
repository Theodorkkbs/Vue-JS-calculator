<template>
<div class="calculator">
  <div class="result">
    {{answer}}
  </div>
  <div class="input">{{inputLog + input}} </div>
  <div @click="clearFunction()" class="btn operator">C</div>
  <div @click="plusminus()" class="btn operator">+/-</div>
  <div @click="percent()" class="btn operator">%</div>
  <div @click="division()" class="btn operator">/</div>

  <div @click="addInput('7')" class="btn">7</div>
  <div @click="addInput('8')" class="btn">8</div>
  <div @click="addInput('9')" class="btn">9</div>
  <div @click="multiply()" class="btn operator">X</div>

  <div @click="addInput('4')" class="btn">4</div>
  <div @click="addInput('5')" class="btn">5</div>
  <div @click="addInput('6')" class="btn">6</div>
  <div @click="minus()" class="btn operator">-</div>

  <div @click="addInput('1')" class="btn">1</div>
  <div @click="addInput('2')" class="btn">2</div>
  <div @click="addInput('3')" class="btn">3</div>
  <div @click="plus()" class="btn operator">+</div>

  <div @click="addInput('0')" class="btn zero">0</div>
  <div @click="decimal()" class="btn">.</div>
  <div 
 @click="equal()" class="btn operator">=</div>


</div>
</template>

<script>

export default {
 
data(){
  return{
    input:'',
    answer:'',
    inputLog:'',
    operator:true,
  }
},
methods:{

addInput(number){
  if(this.operator){
    this.input=''
    this.operator=false
  }
    this.input=`${this.input}${number}`

},

clearFunction(){
  this.input=''
  this.answer=''
  this.inputLog=''

},

plus(){
this.addToinputLog('+')

},

multiply(){
  this.addToinputLog('*')

},
division(){
  this.addToinputLog('/')
},

percent(){
  if(this.input!==''){
    this.input=parseFloat(this.input)/100
  }
},

minus(){
  this.addToinputLog('-')
},

addToinputLog(operator){
  if(this.operator===false){
  this.inputLog+=`${this.input}${operator}`
   this.input=''
   this.operator=true
  }
},

equal(){
if(this.operator===false){
 this.answer= eval(this.inputLog+this.input)
}
},

plusminus(){
if(this.input!==''){
 this.input=this.input.charAt(0)==="-" ? this.input.slice(1) : `-${this.input}`
}
},

decimal(){
  if(this.input.indexOf('.')=== -1){
      this.addInput('.')
 
  }
}
}
}
</script>


<style>

body{
  background-color: #3fa9fc;
  font-family: 'Roboto Condensed', sans-serif;
}

.calculator{
  display: grid;
  grid-template-columns: 50px 50px 50px 50px;
  grid-template-rows: 50px 50px;
  background-color: black;
  width:15%;
  height:50%;
  margin-top: 20%;
  margin-left: 20%;
  top: 0;
  right: 0;
  left: 0;
  bottom: 0;
  margin: auto;
  position: absolute;
  grid-gap:10px ;
  border-radius:20px;
}

.btn:hover{
  cursor: pointer;
}
.btn{
  background-color: cornsilk;
  color: black;
  width:40px;
  height:30px ;
  border-radius:30px;
  text-align: center;
  margin: 10px;
  font-weight: bolder;
  font-size: 18px;
}

.result, .input{
  grid-column: span 4;
  font-size: 40px;
  color: white;
  float: right;

}
.zero{
  grid-column:span 2;
  width: 100px;
}

.operator{
  background-color: orange;
}

</style>
