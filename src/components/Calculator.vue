<template>
  <div class="calculator">
   <div class="display btn">{{current || 0}}</div>
  <div @click="clear" class="btn">C</div>
  <div @click="sign" class="btn ">+/-</div>
  <div @click="percent" class="btn ">%</div>
  <div @click='divide'  class="btn operator">÷</div>
  <div @click="append(7)" class="btn">7</div>
  <div class="btn" @click="append(8)">8</div>
  <div class="btn" @click="append(9)">9</div>
  <div  @click='mult' class="btn operator">x</div>
  <div class="btn" @click="append(4)">4</div>
  <div class="btn" @click="append(5)">5</div>
  <div class="btn" @click="append(6)">6</div>
  <div  @click='sub' class="btn operator">-</div>
  <div class="btn" @click="append(1)">1</div>
  <div class="btn" @click="append(2)">2</div>
  <div class="btn" @click="append(3)">3</div>
  <div  @click='add' class="btn operator">+</div>
  <div class="zero btn" @click="append(0)">0</div>
  <div @click="dot" class= "btn">.</div>
  <div @click="equal" class="btn operator">=</div>
  </div>
</template>

<script>
export default {
  data(){
    return{
      previous:null,
      current:'',
      operator:null,
      operatorClicked:false,

    }
  },
  methods:{
    clear(){
      this.current='';
    },
    sign(){
      this.current=this.current.charAt(0)==='-'? 
      this.current.slice(1) : '-'+ this.current;
    },
    percent(){
      this.current = parseFloat(this.current)/1000;
    },
    append(n){
      if(this.operatorClicked){
        this.current='';
        this.operatorClicked=false;
      }
      this.current=this.current+n;
    },
    dot(){
      if(this.current.indexOf('.') === -1){
        this.append('.');
      }
    },
    setPrevious(){
      this.previous=this.current;
      this.operatorClicked=true;
    },
    divide(){
      this.operator =(a,b) => a/b;
       this.setPrevious();
    },
    mult(){
      this.operator =(a,b)=> a*b;
     this.setPrevious();
    },
    sub(){
      this.operator =(a,b)=> a-b;
      this.setPrevious();
    },
    add(){
      this.operator =(a,b)=> a+b;
      this.setPrevious();
    },
    equal(){
      this.current= this.operator(
        parseFloat(this.previous), 
        parseFloat(this.current)
        );
        this.previous=null;
    }
    
  }
}
</script>


<style scoped>
.calculator{
  margin:0 auto;
  display: grid;
  font-size:20px;
  grid-template-columns: repeat(4,1fr);
  grid-auto-rows: minmax(50px,auto);
  width: 300px;
}
.display{
  grid-column: 1 /5;
  color: #333;
  font-size: 2rem;
  padding-bottom: 10px;
}

.zero{
  grid-column: 1 / 3;
}
.btn{
  border: 0.5px ridge rgb(99, 99, 99);
  padding-top:15px;
  cursor: pointer;
  background: #a19a9a;
  transition: ease-in-out;
}
.btn:hover{
  opacity: 90%;
}
.btn:active{
  transform: scale(0.95);
}
.operator{
  background: #72a0e6;
}
</style>
