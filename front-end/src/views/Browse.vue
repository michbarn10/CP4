<!--<template>
  <div>
    <div class="pure-menu pure-menu-horizontal">
      <ul class="pure-menu-list">
        <li class="pure-menu-item">
          <a @click="select('United States')" href="#" class="pure-menu-link"
            >United States</a
          >
        </li>
        <li class="pure-menu-item">
          <a @click="select('Canada')" href="#" class="pure-menu-link"
            >Canada</a
          >
        </li>
        <li class="pure-menu-item">
          <a @click="select('Mexico')" href="#" class="pure-menu-link"
            >Mexico</a
          >
        </li>
        <li class="pure-menu-item">
          <a @click="select('Brazil')" href="#" class="pure-menu-link"
            >Brazil</a
          >
        </li>
      </ul>
    </div>
    <ProductList :products="products" />
  </div>
</template>-->

<script>/*
import ProductList from "../components/ProductList.vue";
export default {
  name: "Browse",
  components: {
    ProductList,
  },
  data() {
    return {
      country: "",
    };
  },
  computed: {
    products() {
      return this.$root.$data.products
        ? this.$root.$data.products.filter(
            (product) => product.country === this.country
          )
        : [];
    },
  },
  methods: {
    select(country) {
      this.country = country;
    },
  },
};*/
</script>

<template>
  <div class="wrapper">
    <div class="movies">
      <h1>TEST</h1>
      <div v-if="this.$root.$data.movie.length == 0">
        <h1>There are no Movies in your Theatre</h1>
      </div>
      <div v-else>
        <div class="movie" v-for="movie in movieItems" :key="movie.id">
          <div class="info">
            <h1>{{ movie.name }}</h1>
            <h2>{{ movie.rating }}</h2>
            <p>{{ movie.genre }}</p>
          </div>
          <div class="image">
            <img :src="'/Images/Movies/' + movie.image" />
          </div>
          <div class="year">
            <h2>{{ movie.year }}</h2>
          </div>
          <button @click="removeFromTheatre()">Remove From Theatre</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Theatre",
  computed: {
    movieItems() {
      const temp = [];
      for (let i = 0; i < this.$root.$data.movie.length; i++) {
        let alreadyInTheatre = false;
        for (let j = 0; j < temp.length; j++) {
          if (temp[j].id == this.$root.$data.movie[i].id) {
            alreadyInTheatre = true;
            break;
          }
        }
        if (!alreadyInTheatre) {
          temp.push({
            id: this.$root.$data.theatre[i].id,
            name: this.$root.$data.theatre[i].name,
            rating: this.$root.$data.theatre[i].rating,
            image: this.$root.$data.theatre[i].image,
            year: this.$root.$data.theatre[i].year,
            genre: this.$root.$data.theatre[i].genre,
          });
        }
      }

      return temp;
    },
  },
  methods: {
    removeFromTheatre(movie) {
      for (let i = 0; i < this.$root.$data.movie.length; i++) {
        if (this.$root.$data.movie[i].id == movie.id) {
          this.$root.$data.movie.splice(i, 1);
          i = i - 1;
        }
      }
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
  height: 250px;
  width: 200px;
  object-fit: cover;
}

.movie .image {
  display: flex;
  justify-content: center;
  margin-bottom: 5px;
}

.info {
  background: #f2921d;
  color: #000;
  padding: 10px 30px;
  height: 80px;
}

.info h1 {
  font-size: 16px;
}

.info h2 {
  font-size: 14px;
}

.info p {
  margin: 0px;
  font-size: 10px;
}

.rating {
  display: flex;
}

button {
  height: 50px;
  background: #000;
  color: white;
  border: none;
}

.auto {
  margin-left: auto;
}
</style>
