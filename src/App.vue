<template>
  <div id="app">
    <nav class="navbar navbar-expand-md navbar-dark">
      <a class="navbar-brand" href="#">letsblog</a>
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbars"
        aria-controls="navbars"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbars">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item active">
            <a v-if="!isLoggedIn()" class="nav-link" href="/">
              Home
              <span class="sr-only">(current)</span>
            </a>
            <a v-if="isLoggedIn()" class="nav-link" href="/">
              Hello!
              <span class="sr-only">(current)</span>
            </a>
          </li>
          <li class="nav-item">
            <a class="nav-link" to="/posts" href="/posts">Posts</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="/posts/new">New Post</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="/about" tabindex="-1" aria-disabled="true">About</a>
          </li>
          <li class="nav-item dropdown">
            <a
              class="nav-link dropdown-toggle"
              href="#"
              id="dropdown04"
              data-toggle="dropdown"
              aria-haspopup="true"
              aria-expanded="false"
            >Account</a>
            <div class="dropdown-menu" aria-labelledby="dropdown04">
              <a v-if="!isLoggedIn()" class="dropdown-item" href="/signup">Signup</a>
              <a v-if="!isLoggedIn()" class="dropdown-item" href="/login">Login</a>
              <a v-if="isLoggedIn()" class="dropdown-item" href="/logout">Logout</a>
            </div>
          </li>
        </ul>
        <form class="form-inline my-2 my-md-0">
          <input
            class="form-control"
            type="text"
            placeholder="Search"
            v-model="titleFilter"
            list="titles"
          />
          <datalist id="titles">
            <option v-bind:key="post.id" v-for="post in posts">{{post.title}}</option>
          </datalist>
        </form>
      </div>
    </nav>

    <router-view />
  </div>
</template>

<style>
body {
  background: url("../public/y-pattern.png");
}
body h1 h2 h3 li .nav {
  font-family: "Crimson Text", serif;
}

.navbar-brand {
  font-family: "Courgette", cursive;

  padding-right: 3rem;
  padding-left: 1rem;
}

.navbar {
  background-color: #feaf06;
  font-family: "Crimson Text 600", serif;
  font-weight: 600;
}
</style>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      titleFilter: "",
      posts: [],
    };
  },
  created: function() {
    axios.get("/api/posts").then(response => {
      console.log("Success", response.data);
      this.posts = response.data;
    });
  },
  methods: {
    isLoggedIn: function() {
      console.log("Checking if Logged in or out...");
      if (localStorage.getItem("jwt")) {
        return true;
      } else {
        return false;
      }
    },
    getUserId: function() {
      return parseInt(localStorage.getItem("user_id", "name"));
    },
  },
};
</script>
