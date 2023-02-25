<template>
<div>
  <input class=num v-model="num">
  <input class=num v-model="num2">
  <input class=num v-model="num3">
</div>
<div>
  <button @click="countdown"> comenzar </button>
</div>
</template>

<script>
export default {
data() {
    return {
      num: 0,
      num2: 0,
      num3: 0,
    };
  },

methods:{
resta(){
  this.num3 = this.num3 - 1;
},

countdown(){

if(this.num2>0 && this.num3 == 0){
  this.num2 = this.num2 - 1;
  this.num3 = 59;
}

if(this.num>0 && this.num2 == 0 && this.num3 == 0){
  this.num = this.num - 1;
  this.num2 = 59;
  this.num3 = 59;
}

if(this.num>0 && this.num2 == 1 && this.num3 == 0){
  this.num = 0;
  this.num2 = 59;
  this.num3 = 59;
}


let intervalo = setInterval(() => {
  this.resta();
  if(this.num3 == 0 && this.num2 != 0){
    this.num2  = this.num2 - 1;
    this.num3 = 59;
  }

  if(this.num2 == 0 && this.num != 0){
    this.num  = this.num - 1;
    this.num2 = 59;
  }

  if(this.num == 0 && this.num2==0 && this.num3==0){
    clearInterval(intervalo);
  }
  }, 1000);
}
}
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
</style>
