<template>
  <div class="product-info-colors columns is-mobile">
    <div v-for="(color, index) in colors" :key="color[1]" class="column is-flex-mobile is-justify-content-center colorRadio">
      <label class="color">
        <input type="radio" name="colors" :value="color[0]" @click="$emit('change-color', color[0])"/>
        <span class="radio--button" :style="{backgroundColor: '#' + color[1]}" :id="'color-' + (index+1)"></span>
      </label>
    </div>
  </div>
</template>

<script>
export default {
  name: "ShoeColors",
  props: {
    colors: Array
  },
  emits: ['change-color']
}
</script>

<style scoped>
.product-info-colors {
  margin: 0 .75rem 1.5rem .75rem;
}

.color {
  font-size: 2.5rem;
  cursor: pointer;
}

.radio--button {
  display: block;
  width: 40px;
  height: 40px;
  border-radius: 50%;
}

.product-info-colors input {
  display: none;
}

.product-info-colors input:checked + .radio--button {
  background-color: white !important;
}

.product-info-colors input:checked + #color-1 {
  border: 0.25em solid #65CA8D;
}

.product-info-colors input:checked + #color-2 {
  border: 0.25em solid #56AEFF;
}

.product-info-colors input:checked + #color-3 {
  border: 0.25em solid #FFE380;
}

.product-info-colors input:checked + #color-4 {
  border: 0.25em solid #FF5858;
}
</style>