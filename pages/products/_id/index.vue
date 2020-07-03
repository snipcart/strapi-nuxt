<template>
  <div class="container">
    <div v-if="this.product !== null">
      <button class="snipcart-add-item"
        :data-item-id="product.id"
        :data-item-price="product.Price"
        :data-item-url="`${this.$route.fullPath}`"
        :data-item-description="product.Description"
        :data-item-image="`http://localhost:1337${product.Image[0].url}`"
        :data-item-name="product.Name"
        v-bind="customFields">
        Add to cart
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return {
      product: null
    }
  },
  computed: {
    customFields(){
      return this.product["Custom_field"]
        .map((field, index) => Object.entries(field)
          .map(([key, value]) => ({[`data-item-custom${index + 1}-${key.toString().toLowerCase()}`]: value})))
        .reduce((acc, curr) => acc.concat(curr), [])
    }
  },
  created: async function () {
    const res = await fetch(`http://localhost:1337/products/${this.$route.params.id}`)
    this.product = await res.json()
  }
}
</script>

<style>
</style>
