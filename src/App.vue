<template>
  <div id="app">
    <nav class="navbar navbar-expand-md navbar-dark bg-dark">
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
            <a class="nav-link" href="/">
              Home
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
            >
              Account
            </a>
            <div class="dropdown-menu" aria-labelledby="dropdown04">
              <a class="dropdown-item" href="/signup">Signup</a>
              <a class="dropdown-item" href="/login">Login</a>
              <a class="dropdown-item" href="/logout">Logout</a>
            </div>
          </li>
        </ul>
        <form class="form-inline my-2 my-md-0">
          <input class="form-control" type="text" placeholder="Search" />
        </form>
      </div>
    </nav>

    <!-- <div id="nav">
      <router-link to="/">Home</router-link>
      |
      <router-link to="/signup">Signup</router-link>
      |
      <router-link to="/login">Login</router-link>
      |
      <router-link to="/logout">Logout</router-link>
      |
      <router-link to="/posts">Posts</router-link>
      |
      <router-link to="/posts/new">New Post</router-link>
      |
      <router-link to="/about">About</router-link>
    </div> -->
    <router-view />
  </div>
</template>

<style>
body {
  background: url("../public/y-pattern.png");
}
</style>
