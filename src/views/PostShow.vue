<template>
  <div class="post-show">
    <img v-bind:src="post.image" />
    <h3>{{ post.title }}</h3>
    <p>{{ post.body }}</p>
    <button>
      <router-link v-bind:to="`/posts/${post.id}/edit`" tag="button">Edit Post</router-link>
    </button>
    <hr />
  </div>
</template>

<style>
.post-show,
h3,
p {
  font-family: "Crimson Text", serif;
}
</style>

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
