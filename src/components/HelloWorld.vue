<template>

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap" rel="stylesheet">
    <title>The List App</title>
</head>

<body>



<!-- Start Navbar -->
<div>
<nav class="navbar bg-white">
  <div class="container">
    <a class="navbar-brand" href="#">
      <img src="../../Resources/The-List-App-Logo.png" alt="Bootstrap" width="90" height="60">
    </a>
  </div>
</nav>
</div>
<!-- End Navbar -->

<!-- Start Info Content -->
<div class="infoContent">
    <p>Gestioná tu trabajo diario de la mejor manera</p>
</div>

<div class="">
    <div class="row">
        <div class="col-lg-4 col-md-4 col-sm-12 col-xs-12 infoIcons">
            <img src="../../Resources/Cronometro.png" alt="cronometro">
            <p class="infoIconsText">Seteá el tiempo estimado en el que vas a tardar en hacer tus tareas.</p>
        </div>
        <div class="col-lg-4 col-md-4 col-sm-12 col-xs-12 infoIcons">
            <img src="../../Resources/Checkbox.png" alt="cronometro">
            <p class="infoIconsText">Hacé el check list de <br> tus tareas a tiempo.</p>
        </div>
        <div class="col-lg-4 col-md-4 col-sm-12 col-xs-12 infoIcons">
            <img src="../../Resources/Like.png" alt="cronometro">
            <p class="infoIconsText">Mejorá tu performance día a día.</p>
        </div>
    </div>
</div>
<!-- End Info Content -->

<!-- Start Clock -->
<div>
  <input class=num v-model="num">
  <input class=num v-model="num2">
  <input class=num v-model="num3">
</div>
<div>
  <button @click="countdown"> comenzar </button>
</div>    

<!-- End Clock -->


<!-- Start Bubbles -->
   <div class="bubble"></div>
   <div class="bubble"></div>
   <div class="bubble"></div>
   <div class="bubble"></div>
   <div class="bubble"></div>
   <div class="bubble"></div>
   <div class="bubble"></div>
   <div class="bubble"></div>
   <div class="bubble"></div>
   <div class="bubble"></div>
   <div class="bubble"></div>
   <div class="bubble"></div>
   <div class="bubble"></div>
   <div class="bubble"></div>
   <div class="bubble"></div>
   <div class="bubble"></div>
   <div class="bubble"></div>
   <div class="bubble"></div>
   <div class="bubble"></div>
   <div class="bubble"></div>
<!-- Start Bubbles -->



</body>


</html>

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
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap');

*{
    padding: 0px;
    margin: 0px;
    box-sizing: border-box;
}

body{
    width: 100%;
    height: 4000px;
    position: relative;
    justify-content: center;
    align-items: center;
    background: linear-gradient(to bottom, #17c0eb 0%, #32ff7e 100%);
}

.infoContent{
    font-family: 'Roboto', sans-serif;
    font-weight: bolder;
    color: white;
    font-size: 60px;
    margin-top: 100px;
    text-align: center;
}

.infoIcons{
    margin-top: 100px;
    align-items: center;
    text-align: center;
}

.infoIconsText{
    margin-top: 30px;
    font-size: 20px;
    font-family: 'Roboto', sans-serif;
    color: white;
    font-weight: 900;
}

.bubble{
    width: 25px;
    height: 25px;
    border-radius: 50px;
    background: radial-gradient(ellipse at top, rgba(255,255,255,0.1) 0%, rgba(237,237,237,0.4) 100%);
    position: relative;
    border: 1px solid rgba(255,255,255,0.2);
    box-shadow: 5px 5px 10px 0px #00a0b9 ;
    animation: animate_bubbles 10s linear infinite;
}

.bubble:nth-child(even){
    background: radial-gradient(ellipse at bottom, rgba(255,255,255,0.1) 0%, rgba(237,237,237,0.4) 100%);
}

.bubble::before{
    content: '';
    width: calc(100% - 80%);
    height: calc(100% - 70%);
    position: absolute;
    left: 30%;
    top: 20%;
    background: rgba(255,255,255,0.6);
    box-shadow: 0px 0px 15px 5px rgba(255,255,255,0.6);
    transform: rotate(20deg);
}

.bubble:nth-child(even)::before{
    left: 40%;
    top: 60%;
    transform: rotate(-20deg);
}

.bubble:nth-child(1){
    left: -5%;
    width: 100px;
    height: 100px;
    animation-duration: 10s;
}

.bubble:nth-child(2){
    left: 10%;
    width: 80px;
    height: 80px;
    animation-duration: 14s;
}

.bubble:nth-child(3){
    left: 30%;
    width: 40px;
    height: 40px;
    animation-duration: 10s;
}

.bubble:nth-child(4){
    left: 40%;
    width: 100px;
    height: 100px;
    animation-duration: 14s;
}

.bubble:nth-child(5){
    left: 50%;
    width: 80px;
    height: 80px;
    animation-duration: 10s;
}

.bubble:nth-child(6){
    left: 55%;
    width: 40px;
    height: 40px;
    animation-duration: 14s;
}

.bubble:nth-child(7){
    left: 70%;
    width: 100px;
    height: 100px;
    animation-duration: 10s;
}

.bubble:nth-child(8){
    left: 80%;
    width: 60px;
    height: 60px;
    animation-duration: 14s;
}

.bubble:nth-child(9){
    left: 90%;
    width: 40px;
    height: 40px;
    animation-duration: 10s;
}

.bubble:nth-child(10){
    left: 10%;
    width: 70px;
    height: 70px;
    animation-duration: 14s;
}

.bubble:nth-child(11){
    left: -5%;
    width: 100px;
    height: 100px;
    animation-duration: 10s;
}

.bubble:nth-child(12){
    left: 10%;
    width: 80px;
    height: 80px;
    animation-duration: 14s;
}

.bubble:nth-child(13){
    left: 30%;
    width: 40px;
    height: 40px;
    animation-duration: 10s;
}

.bubble:nth-child(14){
    left: 40%;
    width: 100px;
    height: 100px;
    animation-duration: 14s;
}

.bubble:nth-child(15){
    left: 50%;
    width: 80px;
    height: 80px;
    animation-duration: 10s;
}

.bubble:nth-child(16){
    left: 55%;
    width: 40px;
    height: 40px;
    animation-duration: 14s;
}

.bubble:nth-child(17){
    left: 70%;
    width: 100px;
    height: 100px;
    animation-duration: 10s;
}

.bubble:nth-child(18){
    left: 80%;
    width: 60px;
    height: 60px;
    animation-duration: 14s;
}

.bubble:nth-child(19){
    left: 90%;
    width: 40px;
    height: 40px;
    animation-duration: 10s;
}

.bubble:nth-child(20){
    left: 10%;
    width: 70px;
    height: 70px;
    animation-duration: 14s;
}

@keyframes animate_bubbles {
    0%{
        transform: scale(0) translateY(0) rotate(0deg);
        opacity: 0;
    }

    10%{
        transform: scale(0) translateY(500px) rotate(0deg);
        opacity: 1;
    }

    100%{
        transform: scale(1.5) translateY(-2000px) rotate(360deg);
        opacity: 0.5;
    }
}
</style>
