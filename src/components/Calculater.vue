<template>
  <div class="calculater">
      <div class="display">
        {{ current || 0 }}
      </div>
      <div @click="clear" class="btn">⌫</div>
      <div @click="signs" class="btn">+/-</div>
      <div @click="percent" class="btn">%</div>
      <div @click="divide" class="btn sign" >÷</div>
      <div @click="append('7')" class="btn">7</div>
      <div @click="append('8')" class="btn">8</div>
      <div @click="append('9')" class="btn">9</div>
      <div @click="times" class="btn sign">x</div>
      <div @click="append('4')" class="btn">4</div>
    <div @click="append('5')" class="btn">5</div>
    <div @click="append('6')" class="btn">6</div>
    <div @click="minus" class="btn sign" >-</div>
    <div @click="append('1')" class="btn">1</div>
    <div @click="append('2')" class="btn">2</div>
    <div @click="append('3')" class="btn">3</div>
    <div @click="add" class="btn sign" >+</div>
    <div  @click="append('0')" class="btn zero">0</div>
    <div @click="dot" class="btn">.</div>
    <div @click="total" class="btn sign" >=</div>
</div>
</template>

<script>
export default {
    data(){
        return{
            operatorClicked: false,
            previous:null,
            current:'',
            operator: null,
           
        }
    },
    methods:{
        clear(){
            this.current='';
        },
    
    signs(){
        this.current=this.current.charAt(0) ==='-'?
        this.current.slice(1):`-${this.current}`;
    },
    percent(){
        this.current=`${parseFloat(this.current)/100}`
    },
    append(number){
        if(this.operatorClicked){
            this.current='';
            this.operatorClicked=false;
        }
        this.current=`${this.current}${number}`
    },
    dot(){
        if(this.current.indexOf('.')=== -1){
            this.append('.');
        }
    },
    setPrevious(){
        this.operatorClicked=true;
        this.previous=this.current;
    },
    divide(){
        this.operator=(a,b)=>b/a;
        this.setPrevious();
        
        },
    times(){
        this.operator=(a,b)=>a*b;
    this.setPrevious();
    
       },
    add(){
        this.operator=(a,b)=>a+b;
    this.setPrevious();

         },
    minus(){
        this.operator=(a,b)=>b-a;
    this.setPrevious();
    
          },
    total(){
this.current=`${this.operator(parseFloat(this.current),parseFloat(this.previous))}`;
this.previous=null;
    },
    },
}
</script>

<style scoped>

.calculater{
    display: grid;
     width: 400px;
     height: 500px;
     margin: 0 auto;
    grid-template-columns:repeat(4,1fr) ;
   
    gap:10px;
    
   
}
.display{
    display: flex;
    flex-direction: row;
    justify-content: flex-end;
    align-items: center;
    grid-column: 1/5;
    background-color:#333;
    color: azure;
    height: 60px;
    font-size: 24px;
    padding: 0 20px;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.2);
}
.zero{
    grid-column: 1/3;
   
   
}
.btn{
    background-color: #f1f1f1;
    border: none;
    border-radius: 50%;
    font-size:24px;
    cursor: pointer;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
}
.sign{
    background-color: #ff9f0a;
    color: white;
}
.btn:hover{
    background-color: #e5e5e5;
}
</style>