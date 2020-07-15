<template>
  <div class="flex xl:flex-row lg:flex-row md:flex-row sm:flex-col items-center">
    <div v-for="p in products" :key="p.id" class="w-1/3 mt-6 ml-6 mr-6 border rounded-lg">
      <nuxt-link :to="`/products/${p.id}`">
        <div class="rounded-t-lg" :style="{backgroundImage: p.gradient}">
            <img class="crop mx-auto" :src="p.image">
        </div>          
        <div class="ml-4 mt-4 mb-4 mr-4">
          <h4 class="mt-1 font-semibold text-lg leading-tight truncate">{{p.title}}</h4>
          <div class="mt-1">{{p.description}}</div>
        </div>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return {
      products: []
    }
  },
  created: async function () {
    const res = await fetch('https://strapi-snipcart.herokuapp.com/products')
    this.products = await res.json()
  }
}
</script>

<style>
.crop {
  width: 180px;
  height: 180px;
}
</style>
