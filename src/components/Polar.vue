<template functional>
  <div :style="Object.assign({}, props.customstyles, {
    width: props.width,
    height: props.height,
    margin: (-1*parseFloat(props.height)/2) + (props.height.match(/([a-z]*|%)$/)[0]) + ' ' 
          + (-1*parseFloat(props.width)/2) + (props.width.match(/([a-z]*|%)$/)[0]),
    transform: `
      rotate(${props.angle}deg) 
      translate(${props.offset}) 
      rotate(${props.extrarotation - (props.setstraight && props.angle)}deg)`,
    zIndex: props.zindex,
  })">
    <slot />
  </div>
</template>

<script>
export default {
  name: 'vue-polar',
  props: {
    // Custom style object, to be merged with calculated styles.
    // The following properties will be overwritten by calculated properties:
    //   width, height, margin, transform, zIndex, position, top, left
    // Other CSS properties can be used.
    customstyles: {
      type: Object,
      default: () => ({})
    },
    // Translation away from the center point
    offset: {
      type: [Number, String],
      default: '100%'
    },
    // Height of polar element (relative to its own axis)
    height: {
      type: [Number, String],
      default: '50px'
    },
    // Width of polar element (relative to its own axis)
    width: {
      type: [Number, String],
      default: '50px'
    },
    // Reset polar element's own rotation
    setstraight: {
      type: Boolean,
      default: true
    },
    // Additional rotation in degrees
    extrarotation: {
      type: Number,
      default: 0
    },
    // Angle of polar rotation, clockwise from the right
    angle: {
      type: Number,
      default: 0
    },
    zindex: {
      type: Number,
      default: 1
    }
  }
}
</script>

<style scoped>
div {
  position: absolute;
  top: 50%;
  left: 50%;
}
</style>