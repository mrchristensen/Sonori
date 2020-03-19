<template>
  <div class="basewrapper">
    <h1 id="title">Favorites</h1>
    <div class="wrapper">
      <div class="products">
        <div class="product" v-for="(product, index) in products" :key="product.id">
          <div class="info">
            <h1>{{product.title}}</h1>
            <p>Artist: {{product.artist}}</p>
            <p>Album: {{product.album}}</p>
            <p>Genre: {{product.genre}}</p>
          </div>
          <img class="image" v-on:click="removeFromCart(index)" src="/images/heart_pink.png" />
        </div>
      </div>

      <ProductList :products="products" />
      <!-- why won't this work -->

      <p>{{ cartMessage }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "CartList",
  props: {
    products: Array
  },
  methods: {
    removeFromCart(index) {
      this.$root.$data.cart.splice(index, 1);
    }
  },
  computed: {
    cartMessage() {
      if (this.products.length == 0) {
        return "You haven't added any songs to your favs. Hearts some songs to see them here.";
      }
      return "";
    }
  }
};
</script>

<style scoped>
.image {
  height: 40px;
  width: 40px;
  border: 0;
  margin: auto;
}

#title {
  text-align: center;
}

.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}

.products {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.product {
  display: flex;
  /* background: #1ed761; */
  background: #f5f5f5;
  border: 3px solid #1ed761;
  border-radius: 8px;

  margin: 10px;
  margin-top: 50px;
  padding: 20px;
  width: 300px;
}

.info {
  color: #000;
  padding-right: 15px;
}

.info h1 {
  font-size: 19px;
  margin-top: 0;
}

.info p {
  margin: 0px;
  font-size: 18px;
}
</style>