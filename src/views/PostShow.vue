<template>
  <div class="post-show">
    <img v-bind:src="post.image" />
    <h3>{{ post.title }}</h3>
    <p>{{ post.body }}</p>
    <hr />
  </div>
</template>

<style></style>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      message: "Post",
      post: {},
    };
  },
  created: function() {
    axios.get("/api/posts/" + this.$route.params.id).then(response => {
      console.log("Success", response.data);
      this.post = response.data;
    });
  },
  methods: {},
};
</script>
