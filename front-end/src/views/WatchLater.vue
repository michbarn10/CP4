<template>
  <div class="wrapper">
    <div class="movies">
      <div v-if="this.$root.$data.theatre.length == 0">
        <h1>You have no movies to Review.</h1>
      </div>
      <div v-else>
        <div class="movie" v-for="(movie, index) in movieItems" :key="movie.id">
          <div class="image">
            <img :src="require(`@/assets/Movies/${movie.image}`)" />
          </div>
          <div class="info">
            <h1>{{ movie.rating }}</h1>
            <h2>{{ movie.year }}</h2>
            <p>{{ movie.genre }}</p>
          </div>
          <div class="name">
            <h2>{{ movie.name }}</h2>
          </div>
          <div class="review" v-if="movie.review == undefined">
            <div class="reviewName">
              <input
                type="text"
                v-model="reviewName[index]"
                placeholder="Type your name here..."
              />
            </div>
            <input
              type="text"
              v-model="userReview[index]"
              placeholder="Type your review here..."
            />
            <button @click="addReview(index)">Add Review</button>
          </div>
          <div class="displayReview" v-if="movie.review != undefined">
            <p>"{{ movie.review }}"</p>
            <h5>-{{ movie.reviewName }}</h5>
          </div>
          <button @click="removeFromTheatre(index)">
            Remove From Review List
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
//import data from 'mock-data.js';

export default {
  name: "Theatre",
  data() {
    return {
      userReview: [],
      reviewName: [],
    };
  },
  computed: {
    movieItems() {
      return this.$root.$data.theatre;
    },
  },
  methods: {
    removeFromTheatre(index) {
      this.$root.$data.theatre.splice(index, 1);
    },
    addReview(index) {
      let temp = this.$root.$data.theatre[index];
      temp.review = this.userReview[index];
      temp.reviewName = this.reviewName[index];
      this.$root.$data.theatre.splice(index, 1, temp);
    },
  },
};
</script>

<style scoped>
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}

.movies {
  font-family: "Lucida Console", "Courier New", monospace;
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

.movie {
  margin: 10px;
  margin-top: 50px;
  width: 250px;
}

.movie img {
  border: 2px solid #333;
  border-radius: 5px;
  height: 400px;
  width: 250px;
  object-fit: cover;
}

.movie .image {
  display: flex;
  justify-content: center;
  margin-bottom: 5px;
}

.info {
  background: #8d0000;
  color: rgb(255, 255, 255);
  padding: 10px 30px;
  height: 110px;
  border-radius: 5px;
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

.name {
  display: flex;
  justify-content: center;
}

button {
  height: 50px;
  background: #8d0000;
  color: rgb(255, 255, 255);
  border-radius: 5px;
  margin: 5px;
  font-family: "Lucida Console", "Courier New", monospace;
  border: none;
}

.auto {
  margin-left: auto;
}
.review .reviewName input {
  width: 100%;
  height: 30px;
  margin-bottom: 5px;
  border-radius: 5px;
}
.review {
  justify-content: center;
}
.review input {
  width: 100%;
  height: 70px;
  border-radius: 5px;
}
.review button {
  height: 40px;
  background: #1f3ab1;
  color: rgb(255, 255, 255);
  border-radius: 5px;
  margin-top: 5px;
  font-family: "Lucida Console", "Courier New", monospace;
  border: none;
  align-items: center;
}

.displayReview {
  border-radius: 5px;
  border: 2px solid rgb(122, 18, 18);
  padding-left: 10px;
  padding-right: 10px;
}
</style>
