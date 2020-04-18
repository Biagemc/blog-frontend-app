<template>
  <div class="posts-new">
    <div class="container">
      <form v-on:submit.prevent="submit()">
        <h1>New Post</h1>
        <ul>
          <li class="text-danger" v-for="error in errors">{{ error }}</li>
        </ul>
        <div class="row">
          <div class="form-group col-xl-5">
            <label>Title:</label>
            <input type="text" class="form-control" v-model="newPostTitle" />
          </div>
        </div>
        <div class="row">
          <div class="form-group col-xl-8">
            <label for="exampleFormControlTextarea">Content</label>
            <textarea class="form-control" id="exampleFormControlTextarea" rows="3" v-model="newPostBody"></textarea>
          </div>
        </div>
        <div class="row">
          <div class="form-group col-xl-5">
            <label>Image:</label>
            <input type="text" class="form-control" v-model="newPostImageUrl" />
          </div>
        </div>
        <input type="submit" class="btn btn-secondary" value="Submit" />
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
