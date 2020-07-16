<template>
  <div class="flex justify-between ml-6 mr-6">
    <a href="/">
      <span class="emoji">
        🧁
      </span>
    </a>
    <button class="snipcart-checkout">
        <span class="mt-2 text-gray-500">
          (<span class="snipcart-items-count"></span> items - <span class="snipcart-total-price"></span>)
        </span>

        <span class="emoji">🛒</span> 
    </button>
  </div>
</template>
<script>
export default {
}
</script>

<style>
  .emoji {
    font-size: 30px;
  }
</style>
