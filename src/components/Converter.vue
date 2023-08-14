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
          console.log(json[currencys].high)
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

<style scoped></style>