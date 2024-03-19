<template>
  <div class="jishi">
    <button type="primary" @click="start">开始计时</button>
    <h2>{{ n }}</h2>
    <button type="primary" @click="end">结束计时</button>
  </div>
</template>

<script setup>
  import {ref} from 'vue'
  let n = ref(0)
  let time = null
  function start(){
    time = setInterval(()=>{
      n.value++
    },1000)
  }
  function end(){
    clearInterval(time)
  }

</script>

<style>

</style>