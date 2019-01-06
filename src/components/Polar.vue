<template functional>
  <div :style="Object.assign(props.customStyles, {
    width: props.width,
    height: props.height,
    margin: (-1*parseFloat(props.height)/2) + (props.height.match(/([a-z]*|%)$/)[0]) + ' ' 
          + (-1*parseFloat(props.width)/2) + (props.width.match(/([a-z]*|%)$/)[0]),
    transform: `
      rotate(${props.item/props.segments*360+props.zeroAngle}deg) 
      translate(${props.offset}) 
      rotate(-${(props.setStraight && props.item/props.segments*360) + props.zeroAngle + props.extraRotation}deg)`,
  })">
    <slot />
  </div>
</template>

<script>
export default {
  props: {
    customStyles: {
      type: Object,
      default: () => ({})
    },
    offset: {
      type: [Number, String],
      default: '100%'
    },
    height: {
      type: [Number, String],
      default: '50px'
    },
    width: {
      type: [Number, String],
      default: '50px'
    },
    zeroAngle: {
      // Needs to be positive
      type: Number,
      default: 0
    },
    setStraight: {
      type: Boolean,
      default: true
    },
    extraRotation: {
      type: Number,
      default: 0
    },
    item: {
      type: Number,
      default: 2
    },
    segments: {
      type: Number,
      default: 5
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