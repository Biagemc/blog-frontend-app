<template>
  <div class="post-show">
    <img v-bind:src="post.image" />
    <h3>{{ post.title }}</h3>
    <p>{{ post.body }}</p>
    <div>
      <b-button
        v-if="post.user_id === $parent.getUserId()"
        v-bind:href="`/posts/${post.id}/edit`"
      >Edit Post</b-button>
    </div>
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
