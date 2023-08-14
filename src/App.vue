<script setup>
import Converter from "./components/converter.vue";
</script>

<template>
  <div id="app">
    <h1>Currency Converter</h1>
    <div class="line">
      <Converter currency-a="USD" currency-B="BRL" />
      <Converter currency-a="BRL" currency-B="USD" />
    </div>
    <div class="line">
      <Converter currency-a="CAD" currency-B="BRL" />
      <Converter currency-a="BRL" currency-B="CAD" />
    </div>
    <div class="line">
      <Converter currency-a="EUR" currency-B="BRL" />
      <Converter currency-a="BRL" currency-B="EUR" />
    </div>
  </div>
</template>


<style scoped>
#app {
  margin: auto;
  max-width: 900px;
  font-family: sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  font-family: sans-serif;
  color: #000000;
}

.line {
  margin-top: 40px;
  display: flex;
  justify-content: space-around;
}
</style>
