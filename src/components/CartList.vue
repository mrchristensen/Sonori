<template>
  <div class="basewrapper">
    <h1>Cart</h1>
    <div class="wrapper">
      <div class="products">
        <div class="product" v-for="(product, index) in products" :key="product.id">
          <div class="info">
            <h1>{{product.name}}</h1>
            <p>{{product.country}}</p>
          </div>
          <div class="image">
            <img :src="'/images/products/'+product.image" />
          </div>
          <div class="price">
            <h2>{{product.price}}</h2>
            <button v-on:click="removeFromCart(index)" class="auto">Remove</button>
          </div>
        </div>
      </div>
      <p>{{ cartMessage }}</p>
    </div>
    <button id="submitOrder">Submit Order</button>
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
  margin: 10px;
  margin-top: 50px;
  width: 150px;
}

.product img {
  border: 2px solid #333;
  height: 200px;
  width: 150px;
  object-fit: cover;
}

.product .image {
  display: flex;
  justify-content: center;
  margin-bottom: 5px;
}

.info {
  background: #ffd9a3;
  color: #000;
  padding: 10px 30px;
  height: 80px;
}

.info h1 {
  font-size: 16px;
}

.info h2 {
  margin: 0;
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
  height: 30px;
  background: #ab000b;
  color: white;
  border: none;
  margin-left: auto;
  align-self: center;
}

.auto {
  margin-left: auto;
}

#submitOrder {
  height: 50px;
  background: #83cf40;
  margin: initial;
  display: flex;
  margin-top: auto;
  margin-left: auto;
}
</style>