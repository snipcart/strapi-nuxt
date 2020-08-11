<template>
  <div class="flex justify-between m-6">
    <p class="text-xs font-semibold text-gray-600">NUXT.JS & STRAPI STATIC SITE WITH SNIPCART E-COMMERCE.</p>
    <div class="flex">
        <a href="https://twitter.com/snipcart" class="max-w-xs ml-4">
          <Twitter />
        </a>
        <a href="https://facebook.com/Snipcart/" class="ml-3">
          <Facebook />
        </a>
        <a href="https://github.com/snipcart/strapi-nuxt" class="ml-3">
          <Github />
        </a>
    </div>
  </div>
</template>
<script>
import Twitter from "~/components/icons/twitter.vue";
import Github from "~/components/icons/github.vue";
import Facebook from "~/components/icons/facebook.vue";

export default {
    components: {
    Twitter,
    Github,
    Facebook
  }
}
</script>

<style>
  .emoji {
    font-size: 30px;
  }
</style>
