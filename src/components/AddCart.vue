<template>

  <div class="product-actions" :class="{'btn-disabled': !stock}" @click="addToCart(shoeId)">
    <a v-if="added" href="#" class="add-to-cart">Added to cart</a>
    <a v-else-if="stock" href="#" class="add-to-cart">Add to cart</a>
    <a v-else href="#" class="add-to-cart">Out of stock</a>
  </div>
</template>

<script>
import axios from "axios"

export default {
  name: "AddCart",
  props: {
    shoeId: Number,
    stock: Boolean,
    added: Boolean
  },
  methods: {
    async addToCart(id) {
      let self = this
      let headers = {
        'Content-Type': 'application/json'
      }
      let query = JSON.stringify({
        variant_id: id,
        quantity: 1
      })
      await axios.post('https://lugus-hiring.frb.io/cart/add', query, {headers}).then(() => {
        self.$emit('update-cart-btn', true)
        return
      })
    }
  },
  emits: ['update-cart-btn']
}
</script>

<style scoped>
.product-actions {
  display: flex;
  width: 90%;
  max-width: 315px;
  text-align: center;
  margin: 0 auto 40px;
  cursor: pointer;
}

.add-to-cart {
  width: 100%;
  background: #65CA8D;
  border-radius: 30px;
  font-size: 24px;
  font-weight: 600;
  color: white;
  padding: 12px 0;
}

.btn-disabled .add-to-cart {
  background-color: #d4d4d4;
}
</style>