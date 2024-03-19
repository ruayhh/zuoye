<template>
    <div>
      <input type="number" v-model="num1" />
      <input type="number" v-model="num2" />
      <button @click="add">加</button>
      <button @click="subtract">减</button>
      <button @click="multiply">乘</button>
      <button @click="divide">除</button>
      <p>结果: {{ result }}</p>
    </div>
</template>
  
  <script setup>
    import { ref } from 'vue';
  
    const num1 = ref(0);
    const num2 = ref(0);
    const result = ref(0);
  
    const add = () => {
      result.value = parseInt(num1.value) + parseInt(num2.value);
    };
    const subtract = () => {
      result.value = parseInt(num1.value) - parseInt(num2.value);
    };
    const multiply = () => {
      result.value = parseInt(num1.value) * parseInt(num2.value);
    };
    const divide = () => {
      result.value = parseInt(num1.value) / parseInt(num2.value);
    };
  </script>