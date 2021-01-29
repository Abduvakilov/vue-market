<template>
  <Header />
  <div class='content'>
    <div class='product-side'>
      <product-side />
    </div>
    <div class='cart-side'>
      <cart-side />
    </div>
  </div>
</template>

<script>
import CartSide from './components/CartSide.vue'
import Header from './components/Header.vue'
import ProductSide from './components/ProductSide.vue'

export default {
  name: 'App',
  components: {
    Header,
    ProductSide,
    CartSide
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: var(--faint-weak);
  min-height: 100%;  
}
html, body {
  height: 100%;
}
.content {
  overflow: hidden;  /*makes the body non-scrollable (we will add scrolling to the sidebar and main content containers)*/
  display: flex;  /*enables flex content for its children*/
  box-sizing: border-box;
  height: auto;
  width: 100%;
  position: absolute;
  top: 40px;
  bottom: 0;
}
.content > div {
  height: 100%;  /*allows both columns to span the full height of the browser window*/
  flex-direction: column;  /*places the left and right headers above the bottom content*/
  overflow-y: auto;  /*adds scroll to this container*/
  display: flex;
  /* flex-wrap: wrap; */
}

.product-side {
  margin: 0 0 0 30px;
  flex-basis: 0;
  flex-grow: 999;
}

.cart-side {
  flex-basis: 40rem;
  flex-grow: 1;
  background-color: var(--accent-weak);
  padding: 0 20px 20px;
}

</style>
