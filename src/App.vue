<script setup>
import Converter from "./components/converter.vue";
</script>

<template>
  <div id="app">
    <Converter currency-a="USD" currency-B="BRL" />
  </div>
</template>


<style scoped>
#app {
  font-family: sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
