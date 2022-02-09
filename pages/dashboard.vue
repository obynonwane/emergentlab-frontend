<template>
  <div class="container-fluid p-0">
    <v-card color="grey lighten-4" flat height="50px" tile>
      <v-toolbar dense>
        <!-- <v-app-bar-nav-icon></v-app-bar-nav-icon> -->

        <v-toolbar-title>
          <section>
            <v-img class="overlay-img" src="getchangelogo.png"> </v-img>
          </section>
        </v-toolbar-title>

        <v-spacer></v-spacer>

        <v-btn icon>
          <v-icon>mdi-circle</v-icon>
        </v-btn>
        <span>Hi, Joshua</span>
        <v-btn icon>
          <v-icon>mdi-arrow-down</v-icon>
        </v-btn>
      </v-toolbar>
    </v-card>

    <div class="row">
      <div class="col">
        <div class="sidebar">
          <a class="active" href="#home">Home</a>
          <a href="#news">News</a>
          <a href="#contact">Contact</a>
          <a href="#about">About</a>
        </div>
      </div>

      <div class="col"></div>
    </div>
  </div>
</template>

<style scoped>
.container-fluid {
  width: 100vw;
  min-height: 100vh;
  background-color: #e5e5e5;
}

.sidebar {
  margin-right: 120px;
  padding-left: 20px;
  min-height: 100vh;
  background-color: #ffffff;
}




/* The side navigation menu */
.sidebar {
  margin: 0;
  padding: 0;
  width: 100px;
  background-color: #f1f1f1;
  position: fixed;
  height: 100%;
  overflow: auto;
}

/* Sidebar links */
.sidebar a {
  display: block;
  color: black;
  padding: 16px;
  text-decoration: none;
}

/* Active/current link */
.sidebar a.active {
  background-color: #04AA6D;
  color: white;
}

/* Links on mouse-over */
.sidebar a:hover:not(.active) {
  background-color: #555;
  color: white;
}

/* Page content. The value of the margin-left property should match the value of the sidebar's width property */
div.content {
  margin-left: 200px;
  padding: 1px 16px;
  height: 1000px;
}

/* On screens that are less than 700px wide, make the sidebar into a topbar */
@media screen and (max-width: 700px) {
  .sidebar {
    width: 100%;
    height: auto;
    position: relative;
  }
  .sidebar a {float: left;}
  div.content {margin-left: 0;}
}

/* On screens that are less than 400px, display the bar vertically, instead of horizontally */
@media screen and (max-width: 400px) {
  .sidebar a {
    text-align: center;
    float: none;
  }
}
</style>
