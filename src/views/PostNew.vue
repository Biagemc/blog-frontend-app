<template>
  <div class="posts-new">
    <div class="container">
      <form v-on:submit.prevent="submit()">
        <h1>New Post</h1>
        <ul>
          <li class="text-danger" v-for="error in errors">{{ error }}</li>
        </ul>
        <div class="form-group">
          <label>Title:</label>
          <input type="text" class="form-control" v-model="newPostTitle" />
        </div>
        <div class="form-group">
          <label>Content:</label>
          <input type="text" class="form-control" v-model="newPostBody" />
        </div>
        <div class="form-group">
          <label>Image:</label>
          <input type="text" class="form-control" v-model="newPostImageUrl" />
        </div>

        <input type="submit" class="btn btn-primary" value="Submit" />
      </form>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      newPostTitle: "",
      newPostBody: "",
      newPostImageUrl: "",
      errors: [],
    };
  },
  methods: {
    submit: function() {
      let params = {
        title: this.newPostTitle,
        body: this.newPostBody,
        iamge: this.newPostImageUrl,
      };
      axios
        .post("/api/posts", params)
        .then(response => {
          this.$router.push("/posts");
        })
        .catch(error => {
          this.errors = error.response.data.errors;
        });
    },
  },
};
</script>
