<template>
    <div>
      <input type="checkbox" id="juice" value="'果汁'" v-model="selectedDrinks" @change="updateText" />
      <label for="juice">果汁</label>
      <input type="checkbox" id="tea" value="'茶'" v-model="selectedDrinks" @change="updateText" />
      <label for="tea">茶</label>
      <input type="checkbox" id="milk" value="'牛奶'" v-model="selectedDrinks" @change="updateText" />
      <label for="milk">牛奶</label>
      <p>{{ message }}</p>
    </div>
  </template>
  
 <script setup>
  import { ref } from 'vue';
  
  const selectedDrinks = ref([]);
  
  const updateText = () => {
      const selectedItems = selectedDrinks.value;
      message.value = `选中的选项为[${selectedItems}]`;
  }
  
  const message = ref('选中的选项为[]');
</script>
