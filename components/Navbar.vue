<template>
  <div class="">
    <div
      class="m-4 p-6 bg-gray-300 rounded shadow-xl flex flex-row justify-between font-medium items-center"
    >
      <nuxt-link class="text-gray-600 hover:text-gray-800" to="/about"
        >About</nuxt-link
      >
      <nuxt-link class="text-gray-600 hover:text-gray-800" to="/"
        >Home</nuxt-link
      >
      <nuxt-link class="text-gray-600 hover:text-gray-800" to="#"
        ><Hamburger
          class="hover:text-teal-500 transform hover:-rotate-90 transition duration-500 origin-center"
      /></nuxt-link>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style></style>
