<template>
  
  <div class="movies-show">
    <h1>Movie Info</h1>
    <h2>Title: {{ movie.title }}</h2> 
    <p>Year: {{ movie.year }}</p>
    <p>Plot: {{ movie.plot }}</p>
    <p>Director: {{ movie.director }}</p>
    <p>Genre: {{ movie.genre }}</p>
    <!-- <p v-if="movie.genres.length > 1">Genres: {{ movie.genres[0] }}, {{ movie.genres[1] }}</p>
    <p v-else>Genre: {{ movie.genres[0] }} </p> -->
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      movie: {},
    };
  },
  created: function() {
    axios.get(`/api/movies/${this.$route.params.id}`).then((response) => {
      console.log(response.data);
      this.movie = response.data;
    });
  },
};
</script>