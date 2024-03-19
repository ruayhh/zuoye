<template>
    <table border="1" align="center" width="100%" cellpadding="20" cellspacing="0">
      <tbody>
        <tr>
          <td>编号</td>
          <td width="100px">物品名称</td>
          <td>单价</td>
          <td width="100px">数量</td>
          <td>小计</td>
        </tr>
        <tr v-for="(item, index) in items" :key="index">
          <td>{{ item.id }}</td>
          <td width="100px">{{ item.name }}</td>
          <td>{{ item.price }}</td>
          <td>
            <button class="button-left" @click="decreaseQuantity(item)">-</button>
            <span>{{ item.quantity }}</span>
            <button class="button-right" @click="increaseQuantity(item)">+</button>
          </td>
          <td>{{ item.quantity * item.price }}</td>
        </tr>
        <tr>
          <td colspan="4">总计</td>
          <td>{{ total }}</td>
        </tr>
        <tr>
          <td colspan="4"></td>
          <td><button @click="confirmPurchase">确认购买</button></td>
        </tr>
      </tbody>
    </table>
  </template>
  
  <script setup lang="ts">
  import { ref } from 'vue';
  
  interface Item {
    id: string;
    name: string;
    price: number;
    quantity: number;
  }
  
  const items: Item[] = [
    { id: '001', name: '铅笔', price: 2, quantity: 0 },
    { id: '002', name: '橡皮', price: 3, quantity: 0 }
  ];
  
  const total = ref(0);
  
  const increaseQuantity = (item: Item) => {
    if (item.quantity < 5) {
      item.quantity++;
      calculateTotal();
    } else {
      alert('数量超过上限');
    }
  };
  
  const decreaseQuantity = (item: Item) => {
    if (item.quantity > 0) {
      item.quantity--;
      calculateTotal();
    } else {
      alert('数量不能小于0');
    }
  };
  
  const calculateTotal = () => {
    let sum = 0;
    for (const item of items) {
      sum += item.quantity * item.price;
    }
    total.value = sum;
  };
  
  const confirmPurchase = () => {
    alert('购买成功');
  };
  </script>