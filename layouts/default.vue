<template>
    <div class="flex justify-center">
        <div class="max-w-screen-lg flex flex-col min-h-screen w-full">
            <NavBar />
            <Nuxt class="flex-grow"/>
            <Footer />
        </div>
        <div hidden id="snipcart" data-api-key="YmZhZjRiM2MtMzI1ZS00YzQ4LWI5ZWMtYzU4YjZlODU1MWVmNjM3MzQyNDMxNTk5MzczODAz"></div>
    </div>
</template>
<script>
import NavBar from './../components/navbar'
import Footer from './../components/footer'

export default {
  components: { NavBar }
}
</script>
<style>
html {
  font-family:
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  font-size: 20px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}
</style>
