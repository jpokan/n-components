<template>
  <a
    class="text-gray-600 font-semibold hover:text-teal-500 overflow-hidden relative"
    href="#"
    @mouseenter="enter($event)"
    @mouseleave="leave($event)"
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
  },
  data() {
    return {
      direction: 'top',
    }
  },
  methods: {
    enter(event) {
      const span = event.target.children[0]
      span.animate(
        [
          { transform: 'translateY(0px)', opacity: 1 },
          { transform: 'translateY(-25px)', opacity: 0 },
          { transform: 'translateY(-50px)', opacity: 1 },
        ],
        {
          // timing options
          easing: 'cubic-bezier(0.42, 0, 0.58, 1)',
          duration: 300,
        }
      )
    },
    leave(event) {
      const span = event.target.children[0]
      span.animate(
        [
          { transform: 'translateY(0px)', opacity: 1 },
          { transform: 'translateY(25px)', opacity: 0 },
          { transform: 'translateY(50px)', opacity: 1 },
        ],
        {
          // timing options
          easing: 'cubic-bezier(0.42, 0, 0.58, 1)',
          duration: 300,
        }
      )
    },
  },
}
</script>

<style>
.link-top:before {
  /* pointer-events: none; */
  content: attr(data-text);
  position: absolute;
  transform: translateY(50px);
}
.link-top:after {
  /* pointer-events: none; */
  content: attr(data-text);
  position: absolute;
  transform: translateY(-50px);
}
</style>
