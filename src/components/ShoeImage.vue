<template>
  <div class="product-image column">
    <img :src="'https://lugus-hiring.frb.io/storage/shoes-' + color + '.png'" alt="Lugshoes">
  </div>
</template>

<script>
export default {
  name: "ShoeImage",
  props: {
    color: String
  }
}
</script>

<style scoped>
.product-image {
  margin: 5em 5em 0 5em;
  padding: 0;
}
</style>