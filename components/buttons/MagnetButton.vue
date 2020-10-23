<template>
  <button
    class="text-gray-900 font-medium px-8 py-4 border-gray-500 border-2 rounded-full outline-none focus:outline-none"
    @mouseenter="enter($event)"
    @mousemove="magnet($event)"
    @mouseleave="leave($event)"
  >
    {{ text }}
  </button>
</template>

<script>
export default {
  props: ['text'],
  data() {
    return {
      mouseStart: 'null',
      initialPosition: 'null',
      mouse: 'null',
      center: 'null',
      d: 'null',
      startSpeed: 200,
      endSpeed: 200,
    }
  },
  methods: {
    enter(event) {
      event.target.style.transition = `${this.startSpeed}ms ease-out`
      this.mouseStart = { x: event.clientX, y: event.clientY }
    },
    leave(event) {
      event.target.style.transition = `${this.endSpeed}ms ease-in` // cubic-bezier(0.64, 0.57, 0.67, 1.53)
      event.target.style.transform = `translate(0px, 0px)`
    },
    magnet(event) {
      // Set speed after first transition is finished
      setTimeout(() => {
        event.target.style.transition = '0ms'
      }, this.startSpeed)

      // Get top-left initial position (ox, oy)
      // const originX = event.target.offsetLeft
      // const originY = event.target.offsetTop
      // this.initialPosition = { x: originX, y: originY }
      // console.log('top-left:' + originX, originY)

      // Get current mouse position (mx, my) on client
      const mouseX = event.clientX
      const mouseY = event.clientY
      this.mouse = { x: mouseX, y: mouseY }
      // console.log('Mouse: ' + mouseX, mouseY)

      // Get center position (cx, cy) of item
      const centerX = event.target.offsetLeft + event.target.offsetWidth / 2
      const centerY = event.target.offsetTop + event.target.offsetHeight / 2
      this.center = { x: centerX, y: centerY }
      // console.log('Center: ' + centerX, centerY)

      const x = centerX - mouseX
      const y = centerY - mouseY
      // console.log('x=' + x * -1, 'y=' + y * -1)

      // Get distance of mouse to center of item - Just a useful data value and doesn't affect logic
      // this.d = Math.sqrt(Math.pow(x, 2) + Math.pow(y, 2)).toFixed(2)

      const percent = 0.15 // Percentage to move of distance
      event.target.style.transform = `
      translate3d(${-x * percent}px, ${-y * percent}px, 0)
      `
    },
  },
}
</script>

<style></style>
