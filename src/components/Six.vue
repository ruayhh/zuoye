<template>
  <div>
    <p>用户名:<input type="text" name="username" required="required" v-model="username"></p>
    <p>密码:<input type="text" name="password" required="required" v-model="password"></p>
    <br>
    <button v-if="showButton" @click="register">注册</button><br>
    <input type="checkbox"  v-model="isChecked" @change="license"><span>请接受许可协议</span>
    <p>{{ message }}</p>
  </div>
</template>

<script setup>
    import { ref } from 'vue';

    const isChecked = ref(false);
    const showButton = ref(false);
    const username = ref('');
    const password = ref('');
    const message = ref(''); 

    const license = () => {
    showButton.value = isChecked.value;
    };
    const register=()=>{
        if(username.value ==='admin'&& password.value ==='123' ){
            message.value = '注册成功，欢迎admin'
        }else if(username.value === '' || password.value === ''){
            message.value = '用户名和密码不能为空！'
        }else{
            message.value = '用户名或密码错误'
        }
    }

</script>

<style>

</style>