<template>
  <div id="app">
    <Header :cases="cases" :deaths="deaths" :recovered="recovered" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";

export default {
  name: "App",
  components: {
    Header
  },
  data() {
    return {
      cases: undefined,
      deaths: undefined,
      recovered: undefined
    };
  },
  created() {
    fetch("https://coronavirus-19-api.herokuapp.com/all")
      .then(res => res.json())
      .then(data => {
        this.cases = data.cases;
        this.deaths = data.deaths;
        this.recovered = data.recovered;
      })
      .catch(err => console.log(err));
  }
};
</script>

<style>
body {
  overflow-x: hidden;
}
</style>