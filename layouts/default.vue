<template>
  <div class="flex h-screen bg-gray-100">
    <Sidebar
      class="bg-gray-100 w-1/3 lg:w-1/4 xl:w-1/5 z-10 border-r border-gray-300"
    />
    <Nuxt class="w-2/3 lg:w-3/4 xl:w-4/5 z-10" />
    <div
      class="hidden absolute top-0 bottom-0 left-0 right-0 pointer-events-none lg:flex"
    >
      <div class="lg:w-2/4 xl:w-2/5 border-r border-gray-300"></div>
      <div class="lg:w-1/4 xl:w-1/5 border-r border-gray-300"></div>
      <div class="xl:w-1/5 xl:border-r border-gray-300"></div>
    </div>
  </div>
</template>
<script>
export default {}
</script>
<style scoped>
.back {
  z-index: 1;
}
</style>
