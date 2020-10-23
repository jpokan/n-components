<template>
  <div class="flex flex-col">
    <nuxt-link to="/">
      <h2
        class="text-gray-600 font-bold m-4 px-2 text-2xl hover:text-teal-500 transition-colors duration-150"
      >
        Vue/Nuxt UI Components Library
      </h2>
    </nuxt-link>
    <div
      class="m-4 py-4 px-4 flex justify-center gap-4 bg-gray-200 rounded flex-wrap"
    >
      <nuxt-link
        class="hover:text-teal-500 hover:underline text-sm text-gray-600"
        to="/about"
      >
        About
      </nuxt-link>
      <nuxt-link
        class="hover:text-teal-500 hover:underline text-sm text-gray-600"
        to="/"
      >
        Github
      </nuxt-link>
      <nuxt-link
        class="text-sm hover:text-teal-500 font-semibold text-gray-800"
        to="/"
      >
        Donate
      </nuxt-link>
    </div>
    <div class="overflow-y-scroll scrolling-bar">
      <details
        v-for="(type, index) in components"
        :key="index"
        class="mx-4 my-1"
      >
        <summary
          class="px-4 py-2 text-sm font-semibold uppercase text-gray-500 hover:text-teal-500 cursor-pointer transition-colors duration-150 rounded"
        >
          {{ index }}
        </summary>
        <ul>
          <nuxt-link
            v-for="(component, subindex) in type"
            :key="subindex"
            :to="component.path"
          >
            <li
              class="hover:text-teal-500 text-gray-600 hover:bg-gray-200 px-4 py-2 rounded text-sm transition-colors duration-150 capitalize"
            >
              {{ component.name }}
            </li>
          </nuxt-link>
        </ul>
      </details>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      components: null,
    }
  },
  created() {
    function groupBy(objectArray, property) {
      return objectArray.reduce(function (acc, obj) {
        const key = obj[property]
        if (!acc[key]) {
          acc[key] = []
        }
        acc[key].push(obj)
        return acc
      }, {})
    }

    // Return routes of components directory
    const components = this.$router.options.routes.filter((element) => {
      return element.path.includes('/components/')
    })

    // Get list of pages inside components directory
    const paths = components.map((x) => x.path)

    function mutateData(paths) {
      const componentsArray = []

      paths.forEach((path) => {
        const slicedItems = path.split('/').slice(2) // split path and skip index 0, 1 => ["", "components", "type", "name"] => ["type", "name"]
        const component = { type: slicedItems[0], name: slicedItems[1], path }

        componentsArray.push(component)
      })

      const components = groupBy(componentsArray, 'type') // Group components by type
      /* Data follows this structure
      components: {
        buttons: [
          {
            name: 'magnet',
            path: '/components/buttons/magnet',
          },
          {
            name: 'magnet2',
            path: '/components/buttons/magnet2',
          },
        ],
      },
      */
      return components
    }

    this.components = mutateData(paths)
  },
}
</script>

<style scoped>
/* width */
::-webkit-scrollbar {
  width: 1rem;
}

/* Track */
/* ::-webkit-scrollbar-track {
  background: #f1f1f1;
} */

/* Handle */
::-webkit-scrollbar-thumb {
  border: 0.25rem solid #f7fafc;
  background-color: #e2e8f0;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background-color: #38b2ac;
}
</style>
