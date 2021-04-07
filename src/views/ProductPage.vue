<template>
  <div class="columns is-desktop">
    <ShoeImage :color="requestedColor"/>
    <div class="product-info column">
      <ShoeHeading :title="title" v-model:price="price"/>
      <div class="product-info-options">
        <ShoeColors :colors="colors" @change-color="changeColor"/>
        <ShoeSizes :sizes="sizes" @change-size="changeSize"/>
      </div>
      <ShoeDescription :description="description"/>
    </div>
  </div>
  <AddCart :added="added" :shoe-id="stock[0]" :stock="stock[1]" @update-cart-btn="updateCartBtn"/>
</template>

<script>
import ShoeImage from "@/components/ShoeImage";
import ShoeHeading from "@/components/ShoeHeading";
import ShoeColors from "@/components/ShoeColors";
import ShoeSizes from "@/components/ShoeSizes";
import ShoeDescription from "@/components/ShoeDescription";
import AddCart from "@/components/AddCart";

export default {
  name: "ProductPage",
  components: {AddCart, ShoeDescription, ShoeSizes, ShoeColors, ShoeImage, ShoeHeading},
  props: {
    products: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      title: this.products.title,
      description: this.products.description,
      price: 120,
      colors: [
        ['green', '65CA8D'],
        ['blue', '56AEFF'],
        ['yellow', 'FFE380'],
        ['red', 'FF5858']
      ],
      sizes: [
        // Size, quantity, id
        [42, 0, 1],
        [43, 0, 2],
        [44, 0, 3],
        [45, 0, 4],
        [46, 0, 5]
      ],
      requestedColor: 'green',
      stock: [
        1, // id
        false // in stock
      ],
      added: false
    }
  },
  methods: {
    changeColor: function (color) {
      let self = this
      let shoes = self.products.variants
      self.sizes = []
      self.requestedColor = color
      for (let i = 0; i < shoes.length; i++) {
        if (shoes[i].color === color) {
          let shoe = shoes[i]
          self.sizes.push(
              [
                shoe.size,
                shoe.quantity,
                shoe.id
              ]
          )
        }
      }
      return self.sizes
    },
    changeSize: function (size) {
      let self = this
      let shoes = self.products.variants
      self.added = false
      self.stock[0] = size[1]
      self.stock[1] = false
      for (let i = 0; i < shoes.length; i++) {
        if (shoes[i].size === size[0] && shoes[i].color === self.requestedColor) {
          self.price = parseInt(shoes[i].price)
          if (shoes[i].quantity > 0) {
            self.stock[1] = true
          }
          return [
            self.added,
            self.price,
            self.stock
          ]
        }
      }
    },
    updateCartBtn: function (added) {
      if (added) {
        this.added = true
      } else {
        this.added = false
      }
      return this.added
    }
  }
}
</script>

<style scoped>
.product-info-options {
  padding-bottom: 2.5em;
}
</style>