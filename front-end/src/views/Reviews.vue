<template>
  <div v-if="this.reviews.length == 0">
    <h1>There are no reviews to view.</h1>
  </div>
  <div v-else><Review-List /></div>
  <!-- <div v-else><Review-List :reviews="reviews" :movies="movies" /> -->
</template>

<script>
import axios from "axios";
import ReviewList from "../components/ReviewList.vue";
export default {
  name: "Reviews",
  components: {
    ReviewList,
  },
  data() {
    return {
      reviews: [],
      movies: [],
    };
  },
  created() {
    this.getReviews();
  },
  methods: {
    async getReviews() {
      try {
        let response = await axios.get("/api/reviews");
        this.reviews = response.data;
        if (this.reviews) {
          let movieResponse = await axios.get("/api/movies");
          this.reviews.forEach((review) => {
            const movieExists = this.getMovieFromReview(review.movieId);
            if (!movieExists) {
              this.movies.push(
                movieResponse.data.find((movie) => movie.id == review.movieId)
              );
            }
          });
        }
        return true;
      } catch (error) {
        console.log(error);
      }
    },
    getMovieFromReview(movieId) {
      return this.movies.find((movie) => movie.id == movieId);
    },
  },
};
</script>

<style scoped>
h1 {
  font-size: 16px;
  background: #8b0000;
}
</style>
