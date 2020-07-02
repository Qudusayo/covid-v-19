<template>
  <div>
    <div class="jumbotron text-light">
      <div class="container text-center text-uppercase">
        <h1 class="display-3">covid - 19</h1>
        <p>2020 world pandemic disease</p>
      </div>
      <br />
      <br />
      <div v-if="cases">
        <div class="row">
          <Info :value="cases" title="CASES" classes="text-warning" />
          <Info :value="deaths" title="DEATHS" classes="text-danger" />
          <Info :value="recovered" title="RECOVERED" classes="text-success" />
        </div>
      </div>
      <Form v-on:get-info="getInfo" />
    </div>
    <div v-if="country">
      <div class="row container m-auto">
        <Info classes="text-primary" :value="country" title="COUNTRY" />
        <Info classes="text-warning" :value="allcases" title="CASES" />
        <Info classes="text-danger" :value="todayCases" title="TODAY'S CASES" />
        <Info classes="text-danger" :value="alldeaths" title="DEATHS" />
        <Info classes="text-danger" :value="todayDeaths" title="TODAY DEATHS" />
        <Info classes="text-success" :value="allrecovered" title="RECOVERED" />
        <Info classes="text-primary" :value="active" title="ACTIVE" />
        <Info classes="text-warning" :value="critical" title="CRITICAL" />
        <Info classes="text-warning" :value="casesPerOneMillion" title="CASES PER 1 MILLION" />
      </div>
    </div>
  </div>
</template>

<script>
import Form from "./Form.vue";
import Info from "./Info.vue";

export default {
  name: "Header",
  props: ["cases", "deaths", "recovered"],
  components: {
    Form,
    Info
  },
  data() {
    return {
      country: undefined,
      allcases: undefined,
      todayCases: undefined,
      alldeaths: undefined,
      todayDeaths: undefined,
      allrecovered: undefined,
      active: undefined,
      critical: undefined,
      casesPerOneMillion: undefined
    };
  },
  methods: {
    getInfo(country) {
      fetch(`https://coronavirus-19-api.herokuapp.com/countries/${country}`)
        .then(res => res.json())
        .then(response => {
          this.country = response.country;
          this.allcases = response.cases;
          this.todayCases = response.todayCases;
          this.alldeaths = response.deaths;
          this.todayDeaths = response.todayDeaths;
          this.allrecovered = response.recovered;
          this.active = response.active;
          this.critical = response.critical;
          this.casesPerOneMillion = response.casesPerOneMillion;
        })
        .catch(err => console.log(err));
    }
  }
};
</script>

<style scoped>
.jumbotron {
  text-align: center;
  background-color: #1c083d !important;
}
</style>