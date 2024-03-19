<template>
 <div class="sg" >
    <h4>水果列表</h4 >
    <ul>
        <!-- <li>{{ LaStore.talkList }}</li> -->
        <li v-for="sg in sgList" :key="sg.id">
        水果编号：{{ sg.id }}---水果名称：{{ sg.name }}---详细信息：{{ sg.nr }}
        </li>
      </ul>
 </div>
</template>

<script setup>
    import {reactive, ref} from 'vue'
    let sgList = reactive([
        {id:'1',name:'苹果',nr:'苹果汁水丰富，可以生津止渴。'},
        {id:'2',name:'柠檬',nr:'柠檬具有生津止渴、化痰止咳的功效。'}
        ])
</script>

<style>
    .sg{
        padding: 10px;
        border-radius: 5px;
        box-sizing:border-box;
    }
</style>