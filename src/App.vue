<template>



 <router-view>  
   <Home />
 </router-view>
</template>

<script>
import Home from "./views/Home";
export default {
  name:"App",
  components:{
    Home,

}
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
.btn {
  display: inline-block;
  background: white;
  color: black;
  padding: 10px 20px;
  border: none;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
  width: 100px;
 height: 100px;
  
}


</style>
