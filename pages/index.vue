<template>
  <div>
    <p v-for="(item, index) in items" :key="index">{{ item.default.__file }}</p>
  </div>
</template>

<script>
const components = require.context('../components/', true, /\.vue$/)
const cache = {}
function importAll(r) {
  r.keys().forEach((key) => (cache[key] = r(key)))
}
importAll(components)
console.log(cache)

export default {
  data() {
    return {
      items: cache,
    }
  },
}
</script>

<style></style>
