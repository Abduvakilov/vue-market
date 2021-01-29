<template>
<div class='flex'>
  <Category :categories='categories' />
  <ProductList :products='products' />
</div>
</template>

<script>
import Category from './Category.vue'
import ProductList from './ProductList.vue'
export default {
  name: 'Catalogue',
  components: {
    Category,
    ProductList
  },
  data() {
    return {
      categories: {},
      products: {}
    }
  },
  mounted() {
    this.fetchCategories()
      .then(this.fetchProductsAndSort)
      .then(this.countCategory)
  },
  methods: {
    async fetchCategories() {
      return fetch('https://fakestoreapi.com/products/categories')
        .then(response => response.json())
        .then(data => {this.categories = data})
    },
    async fetchProductsAndSort() {
      return fetch('https://fakestoreapi.com/products')
        .then(response => response.json())
        .then(products => {
          for(var i = 0; i < products.length; i++) {
            var category = products[i].category
            if (!(category in this.products)) {
              this.products[category] = []
            }
            this.products[category].push(products[i])
          }
        })
    },
    countCategory() {
      var counts = {}
      for(const [category, array] of Object.entries(this.products)) {
        counts[category] = array.length
      }
      this.categories = counts
    }
  }
}
</script>

<style scoped>
div {
  margin: 20px 10px 30px 0;
}
</style>