<template>
  <div class="flex products">
    <template v-for='categoryProducts in products' :key='categoryProducts'>
      <div class='card flex' v-for='(product, index) in categoryProducts' :key='product.id'>
        <div>
          <img :src='product.image' />
        </div>
        <div class="fg">
          <h3 :class='{weak: index*3%100===0}' > {{product.title}} </h3>
          <div class="flex fg weak">
            <span>{{product.price}} soʻm</span>
            <span class="mla">{{index*3%100}}</span> <!-- Hard coded quantity-->
          </div>
        </div>
      </div>
    </template>
  </div>
</template>

<script>
export default {
  name: 'ProductList',
  props: [
    'products'
  ],

}
</script>

<style scoped>
.products {
  flex-direction: row;
  flex-wrap: wrap;
}
div.card {
  flex-basis: 150px;
  flex-grow: 1;
  margin: 5px;
}
.card img {
  object-fit: cover;
  width: 50px;
  height: 50px;
  margin-right: 15px;
}
span {
  display: inline-block;
}
h3 {
  margin-bottom: 10px;
}
</style>