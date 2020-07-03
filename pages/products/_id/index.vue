<template>
  <div class="container">
    <div v-if="this.product !== null">
      {{this.product.Name}}
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
  created: async function () {
    const res = await fetch(`http://localhost:1337/products/${this.$route.params.id}`)
    this.product = await res.json()
  }
}
</script>

<style>

.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
</style>
