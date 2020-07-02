<template>
  <div class="top">
    <form class="card p-2" @submit="getCountryData">
      <div class="input-group">
        <input
          type="text"
          name="country"
          autocomplete="off"
          class="form-control text-capitalize"
          placeholder="COUNTRY"
          v-model="country"
        />
        <div class="input-group-append">
          <button type="submit" class="btn btn-primary btn-outline-dark text-light">GET INFO</button>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "Form",
  data: function() {
    return {
      country: ""
    };
  },
  methods:{
    getCountryData(e) {
      e.preventDefault();
      this.$emit('get-info', this.country)
    }
  }
};
</script>

<style scoped>
div .top {
  margin-top: "40px";
}
</style>