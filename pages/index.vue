<template>
  <div class="flex xl:flex-row lg:flex-row md:flex-row sm:flex-col items-center">
    <div v-for="p in products" :key="p.id" class="w-1/3 mt-6 ml-6 mr-6 border rounded-lg">
      <nuxt-link :to="`/products/${p.id}`">
        <div :style="{backgroundImage: p.gradient}">
            <img class="mx-auto" :src="`https://strapi-snipcart.herokuapp.com${p.image[0].formats.thumbnail.url}`">
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
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
