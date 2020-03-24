<template>
  <div class="review">
    <div class="review__name">{{ name }}</div>
    <div class="review__subtitle">{{ subtitle }}</div>
    <div class="review__texts">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      default: ''
    },
    subtitle: {
      type: String,
      default: ''
    }
  }
}
</script>