<template>
  <div>
    <div class="pure-menu pure-menu-horizontal">
      <div class="search">
        <form class="pure-form">
          <i class="fas fa-search"></i>
          <input v-model="searchText" />
        </form>
      </div>
      <ul class="pure-menu-list">
        <li class="pure-menu-item">
          <a @click="select('Pop')" href="#" class="pure-menu-link">Pop</a>
        </li>
        <li class="pure-menu-item">
          <a @click="select('Indie')" href="#" class="pure-menu-link">Indie</a>
        </li>
        <li class="pure-menu-item">
          <a @click="select('Country')" href="#" class="pure-menu-link">Country</a>
        </li>
        <li class="pure-menu-item">
          <a @click="select('Classical')" href="#" class="pure-menu-link">Classical</a>
        </li>
        <li class="pure-menu-item">
          <a @click="select('R&B')" href="#" class="pure-menu-link">R&B</a>
        </li>
        <li class="pure-menu-item">
          <a @click="select('Soul')" href="#" class="pure-menu-link">Soul</a>
        </li>
        <li class="pure-menu-item">
          <a @click="select('Dance')" href="#" class="pure-menu-link">Dance</a>
        </li>
        <li class="pure-menu-item">
          <a @click="select('Electronic')" href="#" class="pure-menu-link">Electronic</a>
        </li>
        <li class="pure-menu-item">
          <a @click="select('Metal')" href="#" class="pure-menu-link">Metal</a>
        </li>
        <li class="pure-menu-item">
          <a @click="select('all')" href="#" class="pure-menu-link">All Genres</a>
        </li>
      </ul>
    </div>
    <ProductList :products="products" />
  </div>
</template>

<script>
import ProductList from "../components/ProductList.vue";
export default {
  name: "Browse",
  components: {
    ProductList
  },
  data() {
    return {
      genre: "all",
      searchText: ""
    };
  },
  computed: {
    products() {
      let products = this.$root.$data.products;
      if(this.genre != "all") {
        products = this.$root.$data.products.filter(
          product => product.genre === this.genre
        );
      }
      return products.filter(
        product => product.title.toLowerCase().search(this.searchText) >= 0
      );
    }
  },
  methods: {
    select(genre) {
      this.genre = genre;
    }
  }
};
</script>

<style scoped>
.pure-menu {
  text-align: center;
  margin-left: auto;
  margin-right: auto;
}

.pure-menu-item {
  background-color: #1ed761;
  border-radius: 8px;
  margin: 4px;
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

.search {
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 50%;
  margin-left: auto;
  margin-right: auto;
  margin-top: 16px;
  margin-bottom: 16px;
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