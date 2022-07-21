<script setup lang="ts">
import { ref } from "@vue/reactivity";
import { onMounted } from "@vue/runtime-core";
import axios from "axios"

const data = ref()

interface apiType {
  message: URL;
}

const getApi = () => {
   axios.get<apiType>('https://dog.ceo/api/breeds/image/random')
  .then( res => {
    data.value = res.data
  })
}

onMounted(getApi)
</script>



<template>
  <div class="container">
    <div class="dog_wrapper">
      <button @click="getApi">Photo Change</button>
    <img :src="data.message" alt="">
    </div>
  </div>
</template>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.dog_wrapper{
  display: flex;
  flex-direction: column;
  align-items: center;
  button{
    background-color: #4CAF50; /* Green */
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  cursor: pointer;
  }
  img{
    margin-top: 10px;
    width: 350px;
    height: 350px;
  }
}
</style>
