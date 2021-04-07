<template>
  <p class="product-info-description">{{ description }}</p>
</template>

<script>
export default {
  name: "ShoeDescription",
  props: {
    description: String
  }
}
</script>

<style scoped>
.product-info-description {
  font-size: 14px;
  font-weight: 400;
  margin: 0 .75rem 0 .75rem;
  padding-left: .75rem;
}
</style>