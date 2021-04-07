<template>
  <ul class="product-info-sizes columns is-mobile is-multiline">
    <div v-for="(size, index) in sizes" :key="size[2]" class="column has-text-centered is-flex-mobile"
         :class="calcPosition(index)">
      <li :data-value="size[0]" :data-id="size[2]" :class="{disabled: size[1] === 0}"
          @click="$emit('change-size', [size[0], size[2]]), setActive($event.target)">
        <a href="#">{{ size[0] }}</a>
      </li>
    </div>
  </ul>
</template>

<script>
export default {
  name: "ShoeSizes",
  props: {
    sizes: Array
  },
  methods: {
    calcPosition: function (index) {
      if (index === 0) {
        return ['is-one-third-mobile', 'is-justify-content-flex-end']
      } else if (index === 1) {
        return ['is-one-third-mobile', 'is-justify-content-center']
      } else if (index === 2) {
        return ['is-one-third-mobile', 'is-justify-content-flex-start']
      } else if (index === 3) {
        return ['is-one-half-mobile', 'is-justify-content-flex-end']
      } else if (index === 4) {
        return ['is-one-half-mobile', 'is-justify-content-flex-start']
      }
    },
    setActive: function (target) {
      let siblings = target.parentNode.parentNode.children
      siblings.forEach(function (sibling) {
        sibling.firstChild.classList.remove('selected')
      })
      target.classList.add('selected')
    }
  },
  emits: ['change-size']
}
</script>

<style scoped>
.product-info-sizes li {
  border: 3px solid var(--primary-color);
  border-radius: 6px;
  font-size: 24px;
  font-weight: 600;
  width: 80px;
  cursor: pointer;
}
</style>