<template>
  <div id="app">
    <div id="menu">
      <div id="brand">
        <router-link to="/">
          <img src="./assets/globe.jpeg" />
        </router-link>
      </div>
      <div id="side">
        <router-link to="/">
          <div class="menu-item home">
            <img src="./assets/llamas.jpeg" />
            <p>Home</p>
          </div>
        </router-link>
        <router-link to="/reviews">
          <div class="menu-item">
            <img src="./assets/tv.png" />
            <p>Reviews</p>
          </div>
        </router-link>
      </div>
    </div>
    <router-view />
    <footer>
      <br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
      <a href="https://github.com/michbarn10/CP4">GitHub</a>
    </footer>
  </div>
</template>

<style>
* {
  box-sizing: border-box;
  background: cornsilk;
}

body {
  margin: 50px 100px;
}

#menu {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-column-gap: 5px;
  grid-template-areas: "none brand side";
  margin-bottom: 50px;
}

#brand {
  grid-area: brand;
  display: flex;
  justify-content: center;
}

#side {
  grid-area: side;
  display: flex;
  justify-content: flex-end;
  align-items: center;
}

#side img {
  width: 30px;
  height: 15px;
}

.menu-item {
  display: flex;
  flex-direction: column;
}

.menu-item p {
  margin: 0px;
}

.home {
  margin-right: 10px;
}
</style>
