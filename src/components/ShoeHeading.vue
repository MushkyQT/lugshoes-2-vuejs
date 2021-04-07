<template>
  <div class="product-info-headline columns is-desktop is-vcentered">
    <div class="column is-flex-mobile is-justify-content-center">
      <h1>{{ title }}</h1>
    </div>
    <div class="column is-flex-mobile is-justify-content-center">
      <div class="pricetag">{{ price }}&euro;</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ShoeHeading",
  props: {
    title: String,
    price: Number
  }
}
</script>

<style scoped>
.product-info-headline {
  margin-bottom: 0 !important;
  padding-bottom: 1rem;
}

.product-info-headline > div {
  padding-bottom: 0;
}

h1 {
  font-weight: 600;
  font-size: 36px;
}

.pricetag {
  padding: 4px 14px;
  border-radius: 6px;
  background-color: var(--primary-color);
  color: white;
  font-weight: 600;
  font-size: 18px;
}
</style>