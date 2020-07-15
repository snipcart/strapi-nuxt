<template>
  <div class="flex justify-center">
      <div class="w-2/3 mt-6 ml-6 mr-6 border rounded-lg" v-if="this.product !== null">
        <div>
            <div :style="{backgroundImage: product.gradient}">
            <img class="mx-auto" :src="`https://strapi-snipcart.herokuapp.com${product.image[0].formats.small.url}`">
        </div>          
        <div class="ml-4 mt-4 mb-4 mr-4">
          <h4 class="mt-1 font-semibold text-lg leading-tight truncate">{{product.title}}</h4>
          <div class="mt-1">{{product.description}}</div>

          <button 
            class="snipcart-add-item mt-4 bg-white hover:bg-gray-100 text-gray-800 font-semibold py-2 px-4 border border-gray-400 rounded shadow"
            :data-item-id="product.id"
            :data-item-price="product.price"
            :data-item-url="`${this.$route.fullPath}`"
            :data-item-description="product.description"
            :data-item-image="`https://strapi-snipcart.herokuapp.com${product.image[0].url}`"
            :data-item-name="product.title"
            v-bind="customFields">
            Add to cart
          </button>
        </div>
        </div>
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
      return this.product["custom"]
        .map((field, index) => Object.entries(field)
          .map(([key, value]) => ({[`data-item-custom${index + 1}-${key.toString().toLowerCase()}`]: value})))
        .reduce((acc, curr) => acc.concat(curr), [])
    }
  },
  created: async function () {
    const res = await fetch(`https://strapi-snipcart.herokuapp.com/products/${this.$route.params.id}`)
    this.product = await res.json()
  }
}
</script>

<style>
</style>
