<template>
  <div class="text-gray-700 flex mt-32 mb-20 lg:mt-64 lg:mb-64">
    <div class="w-0 sm:w-1/4"></div>
    <div class="w-full sm:w-2/4 m-10 sm:m-0">
      <client-only>
        <!-- this component will only be rendered on client-side -->
        <h1 class="text-4xl lg:text-6xl font-bold">
          {{ message }}
        </h1>
      </client-only>
      <p class="mt-6 lg::mt-16">This is my Vue UI components library.</p>
    </div>
    <div class="w-0 sm:w-1/4"></div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      index: 0,
      messages: [
        'Hi, looking for components?',
        'Welcome back buddy!',
        'Eat healthy, please ?',
        "Don't forget to sleep.",
        'Are you a developer?',
      ],
    }
  },
  computed: {
    message() {
      return this.messages[this.index]
    },
  },
  mounted() {
    this.changeIndex(this.messages.length)
  },
  methods: {
    random(max) {
      return Math.floor(Math.random() * Math.floor(max))
    },
    changeIndex(length) {
      setInterval(() => (this.index = this.random(length)), 4000)
    },
  },
}
</script>

<style></style>
