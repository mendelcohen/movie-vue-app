<template>
  <div class="movies-new">
    <form v-on:submit.prevent="createMovie()">
      <h1>Add a New Movie</h1>
      <ul>
        <li class="text-danger" v-for="error in errors">{{ error }}</li>
      </ul>
      <div class="form-group">
        <label>Title:</label> 
        <input type="text" class="form-control" v-model="title">
      </div>
      <div class="form-group">
        <label>Year:</label>
        <input type="text" class="form-control" v-model="year">
      </div>
      <div class="form-group">
        <label>Plot:</label>
        <input type="text" class="form-control" v-model="plot">
      </div>
        <small>Plot length must be 10 to 100 characters</small><br>
        <small v-if="plot.length < 11"> {{ 10 - plot.length }} remaining characters</small>
        <small v-else> {{ 100 - plot.length }} remaining characters</small>
      <div class="form-group">
        <label>Director:</label>
        <input type="text" class="form-control" v-model="director">
      </div>
      <div class="form-group">
        <label>Genre:</label>
        <input type="number" class="form-control" v-model="genre">
      </div>
      <input type="submit" class="btn btn-primary" value="Submit">
    </form>
  </div>
</template>
    

<style>
</style>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      errors: [],
      title: "",
      year: "",
      plot: "",
      english: "",
      director: "",
      genre: "",
    };
  },
 
  createMovie: function () {
    var params = {
      title: this.title,
      year: this.year,
      plot: this.plot,
      english: this.english,
      director: this.director,
      genre: this.genre,
    };

    axios.post("/api/movies", params).then((response) => {
      console.log("Success", response.data);
      this.$router.push("/movies");
    }).catch((error) => {
      console.log(error.response.data.errors);
    });
  },
};
</script>

