<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Divination Cards</router-link> |
      <router-link to="/Craft">Craft</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style>
@font-face {
  font-family: "PoEFont";

  src: url("./fonts/Fontin-Regular.otf") format("truetype");
}
body{
  background: #000 url('./images/delirium-bg.jpg') no-repeat top center;
  /* background-size: contain; */
  line-height: 1.3;
  margin: 0;
  transform: translate(-50%, -50%);
  position: absolute; 
  top: 50%; 
  left: 50%;
}
#app {
  font-family: "PoEFont";
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #A38D6D;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #DFCF99;
}

#nav a.router-link-exact-active {
  color: #DFCF99;
}
</style>
