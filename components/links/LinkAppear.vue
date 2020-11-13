<template>
  <a
    class="text-gray-600 font-semibold hover:text-teal-500 focus:text-teal-500 transition-colors duration-500 overflow-hidden relative px-2"
    href="#"
    @mouseenter="enter($event)"
    @mouseleave="leave($event)"
    @focus="enter($event)"
    @blur="leave($event)"
  >
    <span :data-text="text" class="flex link-top">
      {{ text }}
    </span>
  </a>
</template>

<script>
export default {
  props: {
    text: {
      type: String,
      default: 'Link',
    },
    easing: {
      type: String,
      default: 'cubic-bezier(0.42, 0, 0.58, 1)',
    },
  },
  methods: {
    enter(event) {
      const span = event.target.children[0]
      span.animate(
        [
          { transform: `translateY(0px)`, opacity: 1 },
          { transform: `translateY(-25px)`, opacity: 0 },
          { transform: `translateY(-50px)`, opacity: 1 },
        ],
        {
          // timing options
          easing: this.easing,
          duration: 300,
        }
      )
    },
    leave(event) {
      const span = event.target.children[0]
      span.animate(
        [
          { transform: `translateY(0px)`, opacity: 1 },
          { transform: `translateY(25px)`, opacity: 0 },
          { transform: `translateY(50px)`, opacity: 1 },
        ],
        {
          // timing options
          easing: this.easing,
          duration: 300,
        }
      )
    },
  },
}
</script>

<style>
.link-top:before {
  pointer-events: none;
  content: attr(data-text);
  position: absolute;
  transform: translateY(50px);
}
.link-top:after {
  pointer-events: none;
  content: attr(data-text);
  position: absolute;
  transform: translateY(-50px);
}
</style>
