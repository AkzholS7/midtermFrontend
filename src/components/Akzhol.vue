<template>
  <img src="@/assets/alatoo-logo.png" alt="Logo" class="logo" />
  <div class="calculator">
    <div class="display">
      <div v-if="state">
        {{ current || 0}}
        
      </div>
      <div v-else>
        <ul>
          <li v-for="hist in history">
            {{ hist }}
          </li>
        </ul>
      </div>
     
      <div class="container">
    
    <div class="calculator">
    </div>
  </div>

    </div>
    
    <div @click="clear" class="btn">C</div>
    <div @click="sign()" class="btn operator">+/-</div>
    <div @click="persent('%')" class="btn operator">%</div>
    <div @click="append('/')" class="btn operator">/</div>
    <div @click="append('7')" class="btn ">7</div>
    <div @click="append('8')" class="btn ">8</div>
    <div @click="append('9')" class="btn ">9</div>
    <div @click="append('*')" class="btn operator">*</div>
    <div @click="append('4')" class="btn ">4</div>
    <div @click="append('5')" class="btn ">5</div>
    <div @click="append('6')" class="btn ">6</div>
    <div @click="append('-')" class="btn operator">-</div>
    <div @click="append('1')" class="btn ">1</div>
    <div @click="append('2')" class="btn ">2</div>
    <div @click="append('3')" class="btn ">3</div>
    <div @click="append('+')" class="btn operator">+</div>
    <div @click="append('0')" class="btn zero">0</div>
    <div @click="dot()" class="btn ">.</div>
    <div @click="equal()" class="btn operator">=</div>
    <div @click="histories()" class="btn ">history</div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data(){
    return{
      current:'',
      operator:null,
      history:[],
      solve:'',
      state:true

    }
  },
  methods:{
    clear(){
      this.state=true
      this.current=''
    },
    sign(){
      this.current = this.current.charAt(0) === '-' ?
          this.current.slice(1) : `-${this.current}`
    },
    persent(){
      this.current = `${parseFloat(this.current)/100}`
    },
    append(number){
      this.current = `${this.current}${number}`
    },
    dot(){
      if(this.current.indexOf('.')===-1){
        this.append('.')
      }
    },
    equal(){
      this.solve = this.current + '='
      this.current = eval(this.current)
      this.solve = this.solve + `${this.current}`
      this.history.push(this.solve)
      console.log(this.history)
    },
    histories(){
      this.state = false
      this.current = this.history
    }


  }

}
</script>


<style scoped>

.calculator{
  cursor: pointer;
  margin: 0 auto;

  width: 500px;
  font-size: 70px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
}
.display{
  grid-column: 1 / 5;
  background-color: #8a969f;
  color: rgb(57, 53, 53);
}
.btn{
  background-color: #ecf0f1;
  border: 1px solid #c7bdbe;
}
.zero{
  grid-column: 1 / 3;
}
.operator{
  background-color: #110a44;
  color: white;
}
.logo {
  /* position: absolute; */
  top: 20px; /* Adjust this value to position the logo vertically */
  bottom: 40px;
  margin-bottom: 40px;
  left: 942px; /* Adjust this value to position the logo horizontally */
  width: 100px; /* Adjust the width of the logo */
  height: 100px; /* Adjust the height of the logo */
  animation: zoomInOut 4s ease-in-out infinite;

}
@keyframes zoomInOut {
  0% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.2);
  }
  100% {
    transform: scale(1);
  }
}



</style>
