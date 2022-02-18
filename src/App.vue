<template>
  <div id="nav">
    <router-link to="/">Home</router-link> 
    <router-link to="/about">About</router-link>
    <router-link to="/labarea">Lab area</router-link>
    <router-link to="/localapi">Local api</router-link>
  </div>
  <router-view/> <!--here will display content from router views, the home and about-->
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}

#nav {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  padding: 30px;
  background-color: #506274;
  
}

#nav a {
  font-weight: bold;
  color: #ffffff;
  margin-left: 10px;
  background-color: #31cf88;
  padding: 10px;
  border-radius: 20px;
  text-decoration: none;
}

#nav a.router-link-exact-active {
  color: #427fb9;
  
}
</style>
