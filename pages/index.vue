<template>
    <div>
        <div class="m-6 grid grid-cols-1 sm:grid-cols-2 md:grid-cols-2 lg:grid-cols-2 xl:grid-cols-2 gap-4">
            <div v-for="p in products" :key="p.id" class="border rounded-lg bg-gray-100 hover:shadow-lg">
            <nuxt-link :to="`/products/${p.id}`">
                <div class="rounded-t-lg bg-white pt-2 pb-2">
                    <img class="crop mx-auto" :src="p.image">
                </div>          
                <div class="pl-4 pr-4 pb-4 pt-4 rounded-lg">
                <h4 class="mt-1 font-semibold text-base leading-tight truncate text-gray-700">{{p.title}}</h4>
                <div class="mt-1 text-sm text-gray-700">{{p.description}}</div>
                </div>
            </nuxt-link>
            </div>
        </div>
    </div>
</template>

<script>
import productsQuery from '../apollo/queries/product/products'

export default {
  data(){
    return {
      products: []
    }
  },
  apollo: {
    products: {
      prefetch: true,
      query: productsQuery
    }
  }
}
</script>

<style>
.crop {
  width: 180px;
  height: 180px;
}
</style>
