<template>
  <div class="posts">
    <h1>{{ message }}</h1>
    <div v-bind:key="post.id" v-for="post in posts">
      <img v-bind:src="post.image" />
      <h3>{{ post.title }}</h3>
      <p>{{ post.body }}</p>
      <div>
        <b-button v-bind:href="`/posts/${post.id}`">Show Post</b-button>
      </div>
      <hr id="breakline-posts" />
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
#breakline-posts {
  border: dotted black 6px;
  border-bottom: none;
  width: 10%;
  margin: 50px auto;
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
