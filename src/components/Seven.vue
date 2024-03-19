<template>
    <div>
      <p>用户名:<input type="text" name="username" required="required" v-model="username"></p>
      <p>密 码:<input type="text" name="password" required="required" v-model="password"></p>
      <p>验证码:<input type="text" name="code" required="required" v-model="inputCode"><button @click="createCode">{{ randomCode }}</button></p>
      <button @click="login">登录</button>
      <p v-if="showSuccess"><img src="D:\Vue\three-vite\success.png" alt="Success"></p>
        <p v-if="showIncorrect"><img src="D:\Vue\three-vite\incorrect.png" alt="Incorrect"></p>
        <p v-if="showCodeError"><img src="D:\Vue\three-vite\code error.png" alt="Code Error"></p>
    </div>
  </template>
  <script setup>
    import { ref } from 'vue';
    const username = ref('');
    const password = ref('');
    const inputCode = ref('');
    const randomCode = ref(generateRandomCode());
    const showSuccess = ref(false);
    const showIncorrect = ref(false);
    const showCodeError = ref(false);
    function generateRandomCode() {
    var code = '';
    var codeLength = 4;
    var randomChars = new Array('0', '1', '2', '3', '4', '5', '6', '7', '8', '9', 'A', 'B', 'C', 'D', 'E', 
    'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z');
    for (var i = 0; i < codeLength; i++) {
      var index = Math.floor(Math.random() * 36);
      code += randomChars[index];
    }
    return code;
    }
    function createCode() {
        randomCode.value = generateRandomCode();
    }
    function login() {
        if (username.value === '' || password.value === '' || inputCode.value === '') {
        showSuccess.value = false;
        showIncorrect.value = false;
        showCodeError.value = false;
        } else if (username.value === 'admin' && password.value === '123' && inputCode.value.toUpperCase() === randomCode.value) {
        showSuccess.value = true;
        showIncorrect.value = false;
        showCodeError.value = false;
        } else if (username.value !== 'admin' || password.value !== '123') {
        showSuccess.value = false;
        showIncorrect.value = true
        showCodeError.value = false;
        } else {
        showSuccess.value = false;
        showIncorrect.value = false;
        showCodeError.value = true;
        }
    }
</script>