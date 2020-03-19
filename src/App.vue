<template>
  <div id="app">
    <div id="menu">
      <div id="brand">
        <router-link to="/">
          <img src="/images/logo.png" />
        </router-link>
      </div>
      <div id="side">
        <router-link to="/">
          <div class="menu-item home">
            <img src="/images/home.png" />
          </div>
        </router-link>
        <router-link to="/browse">
          <div class="menu-item browse">
            <img src="/images/browse-512.png" />
          </div>
        </router-link>
        <router-link to="/favorites">
          <div class="menu-item favorites">
            <img src="/images/heart.png" />
          </div>
        </router-link>
      </div>
    </div>

    <router-view />

    <!-- Footer -->
    <p class="footer" id="footer-text">
      <a href="https://github.com/mrchristensen/Sonori">https://github.com/mrchristensen/Sonori</a>
    </p>
  </div>
</template>

<script>
export default {
  name: "App",
  computed: {
    numberOfItems() {
      return this.$root.$data.cart.length;
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
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

#menu a {
  color: #b84901;
}

#brand {
  grid-area: brand;
  display: flex;
  justify-content: center;
}

#brand img {
  height: 110px;
}

#side {
  grid-area: side;
  display: flex;
  justify-content: flex-end;
}

#side img {
  width: 50px;
}

.menu-item {
  display: flex;
  flex-direction: column;
  margin-left: 28px;
}

.menu-item p {
  margin: 0px;
  margin-right: 50px;
}

.browse {
}

/* Footer */

.footer {
  margin-top: 50px;
  bottom: 20px;
  height: 20px;
  text-align: center;
  /* opacity: 50%; */
  transition-duration: 0.4s;
}

/* .footer:hover {
  opacity: 100%;
} */
</style>