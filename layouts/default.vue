<template>
  <div class="flex bg-gray-100 flex-col md:flex-row min-h-screen">
    <Sidebar
      class="bg-gray-100 hidden md:flex md:w-1/3 lg:w-1/4 xl:w-1/5 z-10 border-r border-gray-300"
    />
    <Nuxt class="w-full md:w-2/3 lg:w-3/4 xl:w-4/5 z-10" />
    <div
      class="hidden fixed top-0 bottom-0 left-0 right-0 pointer-events-none sm:flex"
    >
      <div
        class="sm:w-1/2 md:w-2/3 lg:w-2/4 xl:w-2/5 border-r border-gray-300"
      ></div>
      <div class="md:w-1/3 lg:w-1/4 xl:w-1/5 md:border-r border-gray-300"></div>
      <div class="xl:w-1/5 xl:border-r border-gray-300"></div>
    </div>
    <Navbar class="md:hidden fixed bottom-0 left-0 right-0 z-50" />
  </div>
</template>
