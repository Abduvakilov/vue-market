<template>
  <SearchBox />
  <Catalogue />
</template>

<script>
import SearchBox from "./SearchBox.vue";
import Catalogue from "./Catalogue.vue";

export default {
  name: "ProductSide",
  components: {
    SearchBox,
    Catalogue,
  },
};
</script>

<style>
</style>