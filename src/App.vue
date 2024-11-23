<script setup>
import Left from './components/Left.vue'
import Right from './components/Right.vue' 
</script>

<template>
  <div id="title">
    <text>玉临超市收银系统</text>
  </div>

  <div id="main">
    <Left></Left>
    <Right></Right>
  </div>


</template>

<style scoped>
#title {
  width: 100%;
  height: 10%;
  font-size: 6em;
  text-align: center;
  border: 2px solid black;
}

#main {
  display: flex;
  height: 90%;
}
</style>