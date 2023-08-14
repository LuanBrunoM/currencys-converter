<script>
export default {
  name: "Converter",
  props: ["currencyA", "currencyB"],
  data() {
    return {
      currencyA_value: "",
      currencyB_value: 0
    };
  },
  methods: {
    convert() {
      let from_to = this.currencyA + "-" + this.currencyB;
      let url = "https://economia.awesomeapi.com.br/last/" + from_to

      fetch(url)
        .then(response => {
          return response.json();
        })
        .then(json => {
          let currencys = this.currencyA + this.currencyB
          let rate = json[currencys].high
          this.currencyB_value = (rate * parseFloat(this.currencyA_value)).toFixed(2)
        });
    }
  }
};

</script>

<template>
  <div class="converter">
    <h2>{{ currencyA }} To {{ currencyB }}</h2>
    <input type="text" v-model="currencyA_value" v-bind:placeholder="currencyA">
    <input type="button" value="Convert" v-on:click="convert">
    <h2>{{ currencyB_value }}</h2>
  </div>
</template>

<!-- <style scoped>
.converter {
  padding: 20px;
  max-width: 300px;
  border-radius: 6px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
}
</style> -->

<style scoped> .converter {
   padding: 20px;
   max-width: 300px;
   border-radius: 6px;
   box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
 }

 .converter h2 {
   font-family: sans-serif;
   color: #007bff;
 }

 .converter input {
   font-family: Arial, sans-serif;
 }

 .converter input[type=text] {
   margin-right: 10px;
   border-radius: 4px;
 }

 .converter input[type=button] {
   background-color: #007bff;
   color: white;
   padding: 3px 5px;
   border-radius: 4px;
   border: none;
   cursor: pointer;
 }

 .converter input[type=button]:hover {
   background-color: #0069d9;
 }
</style>