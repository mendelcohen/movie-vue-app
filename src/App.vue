<template>
  

  <div id="navigation">
  <ul>
    <li><router-link to="/">Home</router-link> </li>
    <li class="active"><router-link to="/about">About</router-link></li>
    <li><span v-if="isLoggedIn()"> 
      <router-link to="/logout">Logout</router-link> 
    </span>
    <span v-else>
      <router-link to="/signup">Signup</router-link>
      <router-link to="/login">Login</router-link> 
    </span></li>
    <li><router-link to="/movies-index">Index Movies</router-link></li>
    <li><router-link to="/movies-new">New Movies</router-link></li>
    <li><router-link to="/movies-show">Show Movies</router-link></li>
    <li><router-link to="/movies-edit">Edit Movies</router-link></li>
  </ul>
  <router-view/>

 
    
  


  <div id="copyright"> Design copyright &copy; 2006 <a href="http://www.nikhedonia.com/" title="SimplyGold">Sadhana Ganapathiraju</a> | <a href="#showcase/free_templates/" title="More Free Templates">Free Templates</a> | <a href="#showcase/commercial_templates/" title="More Commercial Templates">Commercial Templates</a> | <a href="http://validator.w3.org/check/referer" title="Xhtml 1.1 Strict">Xhtml Happy</a> | <a href="http://jigsaw.w3.org/css-validator/check/referer" title="Css 2.0 Strict">Css Happy</a> </div>

</div>


    
  
</template>

<style>

</style>

<script>

export default {
  data: function() {
    return {
      
    };
  },
  methods: {
    isLoggedIn: function() {
      return localStorage.getItem("jwt");
    },
    
  },
};

</script>  