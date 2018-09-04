<template>
  <div>
    
    <center> <router-link :to="{ path: '/login'}" push><h1>Login</h1></router-link><br></center>
    <center><nuxt-link to="/table"><h1>Table</h1></nuxt-link><br></center>
    <center><nuxt-link to="/search"><h1>Search</h1></nuxt-link><br></center>
    
  </div>

</template>
<script>
export default {
  data() {
    return {
      id: 1
    };
  }
};
</script>