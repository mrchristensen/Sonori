<template>
  <div class="wrapper">
    <div class="products">
      <div class="header">
        <img class="image" src="/images/heart_filled.png" alt />
        <p class="title">Title</p>
        <p>Album</p>
        <p>Artist</p>
        <p>Genre</p>
      </div>
      <div class="product" v-for="product in products" :key="product.id">
        <div class="info">
          <img
            v-if="!isFound(product)"
            @click="addToCart(product)"
            class="image"
            src="/images/heart.png"
            alt
          />
          <img
            v-if="isFound(product)"
            @click="removeFromCart(product)"
            class="image"
            src="/images/heart_pink.png"
            alt
          />
          <h1 class="title">{{product.title}}</h1>
          <h1>{{product.album}}</h1>
          <h1>{{product.artist}}</h1>
          <h1>{{product.genre}}</h1>
        </div>
        <hr />
        <!-- <div class="image">
          <img :src="'/images/products/'+product.image" />
        </div>-->
        <!-- <div class="price">
          <h2>{{product.artist}}</h2>
          <button v-on:click="addToCart(product)" class="auto">Add to Cart</button>
        </div>-->
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductList",
  props: {
    products: Array
  },
  methods: {
    addToCart(product) {
      this.$root.$data.cart.push(product);
    },
    removeFromCart(product) {
      var index = this.$root.$data.cart
        .map(x => {
          return x.id;
        })
        .indexOf(product.id);

      this.$root.$data.cart.splice(index, 1);
    },
    isFound(product) {
      var found = false;
      for (var i = 0; i < this.$root.$data.cart.length; i++) {
        if (this.$root.$data.cart[i].id == product.id) {
          found = true;
          break;
        }
      }
      return found;
    }
  }
};
</script>

<style scoped>
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}

.header {
  display: flex;
  align-items: center;

  margin-left: auto;
  margin-right: auto;
  margin-top: 10px;
  margin-bottom: 0px;

  width: 1000px;
  /* margin-left: 12px; */
  background: #1ed761;
  color: #000;
  padding-right: 30px;
  height: 40px;

  border-top-left-radius: 25px;
  border-top-right-radius: 25px;
}

.header p {
  font-size: 16px;
  width: 25em;
  text-justify: auto;
  text-align: center;
}

.products {
  margin-top: 20px;
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  justify-content: center;
  width: 1000px;
}

.product {
  margin: 10px;
  margin-top: 0px;
  margin-bottom: 0px;
  width: 1000px;
}

.product img {
  border: 2px solid #333;
  height: 250px;
  width: 200px;
  object-fit: cover;
}

.product .image {
  display: flex;
  justify-content: center;
  margin-bottom: 5px;
}

.product hr {
  padding: 0;
  margin: 0;
}

.info {
  display: flex;
  background: #f5f5f5;
  color: #000;
  padding-right: 30px;
  /* height: 40px; */
}

.info .image {
  height: 40px !important;
  width: 40px !important;
  border: 0 !important;
  padding-top: 3px !important;
  padding-left: 0 !important;
  margin-left: 5px !important;
  margin-right: 18px !important;
}

.header .image {
  height: 25px !important;
  width: 22px !important;
  border: 0 !important;
  padding-top: 3px !important;
  padding-left: 0 !important;
  margin-left: 14px !important;
  margin-right: 25px !important;
}

.info h1 {
  font-size: 16px;
  width: 25em;
  text-justify: auto;
  text-align: center;
  margin: auto;
}

.info h2 {
  font-size: 14px;
}

.info p {
  margin: 0px;
  font-size: 10px;
}

.price {
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