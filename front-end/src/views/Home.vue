<template>
  <div>
    <div class="wrapper">
      <div class="search">
        <form class="pure-form">
          <i class="fas fa-search"></i
          ><input
            v-model="searchText"
            placeholder="What movie are you looking to Review?"
          />
        </form>
      </div>
    </div>
    <Movie-List :movies="movies" />
  </div>
</template>

<script>
import MovieList from "../components/MovieList.vue";
export default {
  name: "Home",
  components: {
    MovieList,
  },
  data() {
    return {
      searchText: "",
    };
  },
  computed: {
    movies() {
      return this.$root.$data.movies
        ? this.$root.$data.movies.filter(
            (movie) =>
              movie.name.toLowerCase().search(this.searchText.toLowerCase()) >=
              0
          )
        : [];
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

.search {
  border: 2px solid rgb(122, 18, 18);
  border-radius: 5px;
  width: 50%;
}

form {
  display: table;
  width: 100%;
}

i {
  display: table-cell;
  padding-left: 10px;
  width: 1px;
}

input {
  display: table-cell;
  font-size: 20px;
  border: none !important;
  box-shadow: none !important;
  width: 100%;
  height: 40px;
}

button {
  font-family: "Lucida Console", "Courier New", monospace;
}
</style>
