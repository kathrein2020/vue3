

<template>
  <div class="wrapper">
  <h1>погода </h1>
  <p>узнать погоду в городе {{ city == "" ? "вашем городе" : "<<"+city+">>" }}</p>
  <input type="text" v-model="city" placeholder=" город">
  <!-- <button v-show="city != ''">получить погоду</button> -->

  <button v-if="city !=''">получить погоду</button>
  <button disabled v-else>введите название города </button>
</div> 
</template>



<script>
export default{
  data(){
    return {
      city: ""
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

</style>