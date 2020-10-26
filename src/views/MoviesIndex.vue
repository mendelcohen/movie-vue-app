<template>
  <div class="movies-index">
    <h1>All Movies</h1>
    <div>
	<button>Sort Alphabetically</button>
    </div>

  Search by name: <input v-model="titleFilter" list="titles">
<datalist id="titles">
	<option v-for="movie in movies">{{ movie.title }}</option>
</datalist>
  <!-- Search by title: <input v-model="titleFilter"><br> -->
   <!-- <div v-for="movie in orderBy(movies, 'title')">  -->
  <div v-for="movie in orderBy(filterBy(movies, titleFilter, 'title'), 'title')">
     <h2>Title: {{ movie.title }}</h2> 
     <p>Year: {{ movie.year }}</p>
     <p>Plot: {{ movie.plot }}</p>
     <p>Director: {{ movie.director }}</p>
     <p v-if="movie.genres.length > 1">Genres: {{ movie.genres[0] }}, {{ movie.genres[1] }}</p>
     <p v-else>Genre: {{ movie.genres[0] }} </p>
   </div>

  
    
   

    
  </div>
</template>


<script>
import axios from "axios";
import Vue2Filters from "vue2-filters";

export default {
  mixins: [Vue2Filters.mixin],
  data: function() {
    return {
      movies: [],
      titleFilter: "",
    };
  },
  created: function() {
    axios.get("api/movies").then((response) => {
      console.log(response.data);
      this.movies = response.data;
    });
  }
};
</script>