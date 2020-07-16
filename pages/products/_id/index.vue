<template>
  <div class="flex justify-center">
      <div class="w-2/3 mt-6 ml-6 mr-6 border rounded-lg" v-if="this.product !== null">
        <div>
            <div class="rounded-t-lg" :style="{backgroundImage: product.gradient}">
            <img class="mx-auto" :src="product.image" width="500">
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
            :data-item-image="product.image"
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
import productQuery from '../../../apollo/queries/product/product'

export default {
  data(){
    return {
      product: null
    }
  },
  computed: {
    customFields(){
      return this.product["custom"]
        .map(({title, required, options}) => ({name: title, required, options}))
        .map((x, index) => Object.entries(x)
          .map(([key, value]) => ({[`data-item-custom${index + 1}-${key.toString().toLowerCase()}`]: value})))
        .reduce((acc, curr) => acc.concat(curr), [])
        .reduce((acc, curr) => ({...acc, ...curr}))
    }
  },
  apollo: {
    product: {
      prefetch: true,
      query: productQuery,
      variables () {
        return { id: parseInt(this.$route.params.id) }
      }
    }
  }
}
</script>

<style>
</style>
