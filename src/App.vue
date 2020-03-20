<template>
  <div id="app">
    <div id="menu">
      <div id="brand">
        <router-link to="/">
          <img @click="changePage('home')" src="/images/logo.png" />
        </router-link>
      </div>
      <div id="side">
        <router-link to="/">
          <div class="menu-item home">
            <img @click="changePage('home')" class="icon" :src="homeIcon"/>
          </div>
        </router-link>
        <router-link to="/browse">
          <div class="menu-item browse">
            <img @click="changePage('browse')" class="icon" :src="browseIcon" />
          </div>
        </router-link>
        <router-link to="/favorites">
          <div class="menu-item favorites">
            <img @click="changePage('heart')" class="icon" :src="favoritesIcon" />
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
  methods: {
    changePage(page) {
      this.$root.$data.currentPage = page;
    }
  },
  computed: {
    numberOfItems() {
      return this.$root.$data.cart.length;
    },
    homeIcon() {
      if(this.$root.$data.currentPage == "home") {
        return '/images/home_filled.png';
      }
      else {
        return '/images/home.png';
      }
    },
    favoritesIcon() {
      if(this.$root.$data.currentPage == "heart") {
        return '/images/heart_filled.png';
      }
      else {
        return '/images/heart.png';
      }
    },
    browseIcon() {
      if(this.$root.$data.currentPage == "browse") {
        return '/images/browse_filled.png';
      }
      else {
        return '/images/browse-512.png';
      }
    }
  }
};
</script>

<style>
.icon:hover {
  opacity: 0.5;
}

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