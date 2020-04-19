<template>
  <div class="posts-edit">
    <div class="container">
      <form v-on:submit.prevent="submit()">
        <h1>Edit Post</h1>
        <ul>
          <li class="text-danger" v-for="error in errors">{{ error }}</li>
        </ul>
        <div class="row">
          <div class="form-group col-xl-5">
            <label>Title:</label>
            <input type="text" class="form-control" v-model="post.title" />
          </div>
        </div>
        <div class="row">
          <div class="form-group col-xl-8">
            <label for="exampleFormControlTextarea">Content</label>
            <textarea
              class="form-control"
              id="exampleFormControlTextarea"
              rows="3"
              v-model="post.body"
            ></textarea>
          </div>
        </div>
        <div class="row">
          <div class="form-group col-xl-5">
            <label>Image:</label>
            <input type="text" class="form-control" v-model="post.image" />
          </div>
        </div>
        <input type="submit" class="btn btn-secondary" value="Submit" />
      </form>
      <b-button v-on:click="deletePost()" class="btn btn-danger">Delete Post</b-button>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      post: {},
      errors: [],
    };
  },
  created: function() {
    console.log("in created on edit page");
    axios.get(`/api/posts/${this.$route.params.id}`).then(response => {
      console.log(response.data);
      this.post = response.data;
    });
  },
  methods: {
    submit: function() {
      let params = {
        title: this.post.title,
        body: this.post.body,
        image: this.post.image,
      };
      axios
        .patch(`/api/posts/${this.post.id}`, params)
        .then(response => {
          this.$router.push("/posts");
        })
        .catch(error => {
          this.errors = error.response.data.errors;
        });
    },
    deletePost: function() {
      console.log("Deleting this post...");
      axios.delete(`/api/posts/${this.post.id}`).then(response => {
        console.log(response.data);
        this.$router.push("/posts");
      });
    },
  },
};
</script>
