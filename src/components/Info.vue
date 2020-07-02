<template>
  <div class="col-md-4">
    <div class="card mb-4">
      <div class="card-body text-center" v-bind:class="classes">
        <h1 class="display-4">{{ value }}</h1>
        <p class="card-text">
          <b>{{ title }}</b>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    name: 'Info',
    props: ['value', 'title', 'classes']
}
</script>