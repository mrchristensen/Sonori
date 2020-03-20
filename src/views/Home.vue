<template>
  <div>
    <div class="wrapper">
      <!-- <div class="search">
        <form class="pure-form">
          <i class="fas fa-search"></i>
          <input v-model="searchText" />
        </form>
      </div>-->
    </div>
    <!-- <ProductList :products="products" /> -->

    <div id="main-page-content">
      <div id="intro">
        <h1>Welcome to Sonori</h1>

        <p
          id="intro-desc"
        >Welcome to Sonori, the lastest up and coming music platform. Sonori boasts the most steamy and hot songs currently released. Diamo inizio alla festa!</p>

        <ul class="pure-menu-list">
          <li class="pure-menu-item">
            <router-link to="/browse">
              <a @click="changePage('browse')" class="pure-menu-link">Browse by Genre</a>
            </router-link>
          </li>
          <li class="pure-menu-item">
            <router-link to="/favorites">
              <a @click="changePage('heart')" class="pure-menu-link">See my Favorites</a>
            </router-link>
          </li>
        </ul>
      </div>

      <img id="cooking-picture" src="images\landing-image.jpg" alt="This could be you" />
    </div>
  </div>
</template>

<script>
// import ProductList from "../components/ProductList.vue";
export default {
  name: "Home",
  methods: {
    changePage(page) {
      this.$root.$data.currentPage = page;
    }
  }
};
</script>

<style scoped>
#intro {
  max-width: 550px;
  display: flex;
  justify-content: center;
  align-content: center;
  flex-direction: column;
  margin-left: 19px;
  margin-right: 19px;
  text-align: center;
}

#intro-desc {
  padding-top: 14px;
  padding-bottom: 14px;
  padding-left: 42px;
  padding-right: 42px;
}

#cooking-picture {
  max-width: 1000px;
  width: 45%;
  height: 45%;
  border: 6px solid #1ed761;
  border-radius: 8px;
  transition-duration: 0.3s;
}

#cooking-picture:hover {
  box-shadow: 0 10px 12px 0 rgba(0, 0, 0, 0.24),
    0 14px 42px 0 rgba(0, 0, 0, 0.19);
}

.pure-menu-list {
  display: flex;
  flex-direction: column;
  margin-left: auto;
  margin-right: auto;
}

.pure-menu {
  text-align: center;
}

.pure-menu-item {
  background-color: #1ed761;
  border-radius: 8px;
  margin: 4px;
  width: 160px;
}

.pure-menu-item a {
  color: #ffffff;
}

.pure-menu-item :hover {
  background-color: #0ec751;
  border-radius: 8px;
}

.pure-menu-item :focus {
  background-color: #31e874;
  border-radius: 8px;
}

#main-page-content {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  margin: 26px;
}

.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}

.search {
  border: 1px solid #ccc;
  border-radius: 4px;
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
</style>