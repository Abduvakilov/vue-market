<template>
  <div class="card cart-items" v-if="cart!==null">
    <div class="header">
      <h1>Cart #{{cart.id}}</h1>
      <button>+</button>
    </div>
    <CartList :products='cart.products' @removeProductFromCart='removeProductFromCart' />
  </div>
  <div class="card" v-else>
    <h1>Loading...</h1>  
  </div>
</template>

<script>
import CartList from './CartList.vue';

export default {
  name: 'CartItems',
  props: [
    'cart'
  ],
  components: {
    CartList,
  },
  methods: {
    removeProductFromCart(key) {
      this.$emit('removeProductFromCart', key)
    }
  }
}
</script>

<style scoped>
.card {
  padding: 20px 30px;
}
.header {
  display: flex;
  margin: 30px 0 10px 0;
}

h1 {
  flex-grow: 1;
  text-align: center;
}

button {
  margin-left: 20px;
}

</style>