<template>
<div class='column'>
  <div class='card category' v-for='(count, category) in categories' :key='category'>
    <a href='#'>
      {{category}} <span class='weak'> {{count}} </span>
    </a>
  </div>
</div>
</template>

<script>
export default {
  name: 'Category',
  props: [
    'categories'
  ],
}
</script>

<style>
.column {
  flex: 0 0 10rem;
}
.category.card {
  line-height: 1.5;
  margin-bottom: 10px;
  padding: 25px;
  border: 2px solid var(--complement-strong);
  text-transform: capitalize;
}
</style>