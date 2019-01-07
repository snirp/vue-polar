<template functional>
  <div :style="Object.assign({}, props.customStyles, {
    width: props.width,
    height: props.height,
    margin: (-1*parseFloat(props.height)/2) + (props.height.match(/([a-z]*|%)$/)[0]) + ' ' 
          + (-1*parseFloat(props.width)/2) + (props.width.match(/([a-z]*|%)$/)[0]),
    transform: `
      rotate(${props.item/props.segments*360+props.zeroAngle}deg) 
      translate(${props.offset}) 
      rotate(${(props.setStraight && -props.item/props.segments*360 - props.zeroAngle) + props.extraRotation}deg)`,
    zIndex: props.zIndex,
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
    customStyles: {
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
    // Starting angle relative to default zero angle (right / east)
    zeroAngle: {
      type: Number,
      default: 0
    },
    // Reset polar element's own rotation
    setStraight: {
      type: Boolean,
      default: true
    },
    // Additional rotation in degrees
    extraRotation: {
      type: Number,
      default: 0
    },
    // Number of equal subdivisions of 360 degrees. Can be a decimal number.
    // A positive number: clockwise rotation
    // A negative number: counter-clockwise rotation 
    segments: {
      type: Number,
      default: 12
    },
    // Cardinal number that determines relative rotation
    // Relative angle is calculated by: item/segments * 360
    item: {
      type: Number,
      default: 0
    },
    zIndex: {
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