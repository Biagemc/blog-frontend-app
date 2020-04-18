<template>
  <div class="home">
    <h1>{{ message }}</h1>
  </div>
</template>

<style>
.home h1 {
  padding-top: 4rem;
  text-align: center;
  font-family: "Crimson Text", serif;
}
</style>

<script>
export default {
  data: function() {
    return {
      message: "Welcome to your blog",
    };
  },
  created: function() {},
  methods: {},
};
</script>
