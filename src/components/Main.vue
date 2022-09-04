<template>
    <div>
        <h1>首页</h1>
        <img alt="Vue logo" src="../assets/logo.png">
        <HelloWorld msg="Welcome to Your Vue.js App">
        </HelloWorld>
    </div>
</template>

<script>
import HelloWorld from './HelloWorld.vue'
export default {
        name: "MainComponent",
        components: {
            HelloWorld
        }
  }
    
</script>

<style scoped>
</style>
