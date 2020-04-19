<template>
  <div class="posts">
    <h1>{{ message }}</h1>
    <div v-bind:key="post.id" v-for="post in posts">
      <img v-bind:src="post.image" />
      <h3>{{ post.title }}</h3>
      <p>{{ post.body }}</p>
      <button class="btn btn-secondary">
        <router-link v-bind:to="`/posts/${post.id}`" tag="button">Show Post</router-link>
      </button>
      <hr />
    </div>
  </div>
</template>

<style>
.posts,
h1,
h3,
p {
  font-family: "Crimson Text", serif;
}

.posts {
  text-align: center;
  padding-top: 2rem;
}
</style>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      message: "Posts",
      posts: [],
    };
  },
  created: function() {
    axios.get("/api/posts").then(response => {
      console.log("Success", response.data);
      this.posts = response.data;
    });
  },
  methods: {},
};
</script>
