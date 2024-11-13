

<template>
  <div class="wrapper">
  <h1>погода </h1>
  <p>узнать погоду в городе {{ city == "" ? "вашем городе" : cityName }}</p>
  <input type="text" v-model="city" placeholder=" город">
  <!-- <button v-show="city != ''">получить погоду</button> -->

  <button v-if="city !=''" @click="getWeather()">получить погоду</button>
  <button disabled v-else>введите название города </button>

  <p class="error">{{ error }}</p>

  <p v-show="info !=null">{{ info.data}}</p>
</div> 
</template>



<script>

import axios from 'axios'

export default{
  data(){
    return {
      city: "",
      error: " ",
      info: null
    }
  },


  //для кавычек сити
  computed : {
    cityName() {
      return "<<" + this.city + ">>"
    }
  },

  methods: {
    getWeather(){
      // если буков меньше 2х то ошибка

if (this.city.trim().length <2) {
  this.error="нужно название более одного символа"
  return false

}

this.error=""

axios.get(`https://weather.visualcrossing.com/VisualCrossingWebServices/rest/services/timeline/${this.city}?key=X4AUKJYNGJYW36MU2H9QYRY8G`)
.then(res => (this.info = res))    

}
  }
}


</script> 

<style scoped>
.wrapper {
  width:900px;
  height: 500px;
  border-radius: 50px;
  padding: 20px;
  background: #1f0f24;
  text-align: center;
  color: white;

  }

  .wrapper h1 {
    margin-top: 50px;
  }

  .wrapper p {
    margin-top: 20px;
  }


  .wrapper input:focus {
    border-bottom-color: blueviolet; 
  }

  .wrapper input {
    margin-top: 30px;
    background: transparent;
    border:0;
    border-bottom: 2px solid #110813;
    color: white;
    font-size: 14px;
    padding: 5px 8px;
    outline: none;
  }

  .wrapper button {
    background: #e3bc4b;
    color: #fff;
    border-radius: 10px;
    border: 2px solid #b99935;
    padding: 10px 15px;
    margin-left: 20px;
    cursor: pointer;
    transition:  transform 500ms ease;
  }

  .wrapper button:hover {
    transform: scale(1.1) translateY(-5px);

    }

  .wrapper button:disabled{
    background: #746027;
    cursor: not-allowed;
  }

  .error {
    font-size:20px;
    color: red;
  }

</style>