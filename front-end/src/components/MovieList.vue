<template>
  <div class="wrapper">
    <div class="movies">
      <div class="movie" v-for="movie in movies" :key="movie.id">
        <div class="image">
          <img :src="require(`@/assets/Movies/${movie.image}`)" />
        </div>
        <div class="info">
          <h1>{{ movie.rating }}</h1>
          <h2>{{ movie.year }}</h2>
          <p>{{ movie.genre }}</p>
        </div>
        <div class="name">
          <h3>{{ movie.name }}</h3>
          <button @click="addToTheatre(movie)">Add to Review List</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MovieList",
  props: {
    movies: Array,
  },
  methods: {
    addToTheatre(movie) {
      if (this.$root.$data.theatre.includes(movie)) {
        return;
      }
      this.$root.$data.theatre.push(movie);
    },
  },
};
</script>

<style scoped>
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: "Lucida Console", "Courier New", monospace;
}

.movies {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

.movie {
  margin: 10px;
  margin-top: 50px;
  width: 200px;
}

.movie img {
  border: 2px solid #333;
  border-radius: 5px;
  height: 250px;
  width: 200px;
  object-fit: cover;
}

.movie .image {
  display: flex;
  justify-content: center;
  margin-bottom: 7px;
}

.info {
  background: #8b0000;
  border-radius: 5px;
  color: rgb(255, 255, 255);
  padding: 10px 30px;
  height: 110px;
}

.info h1 {
  font-size: 16px;
  background: #8b0000;
}

.info h2 {
  font-size: 14px;
  background: #8b0000;
}

.info p {
  margin: 0px;
  font-size: 10px;
  background: #8b0000;
}

button {
  height: 50px;
  background: #8b0000;
  border-radius: 5px;
  color: white;
  border: none;
  font-family: "Lucida Console", "Courier New", monospace;
}

.auto {
  margin-left: auto;
}
</style>
