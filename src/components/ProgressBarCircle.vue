<template>
  <div id="progress-bar-circle">
    <div :style="textStyleCircle">
      {{ value + '%' }}
    </div>
    <svg
      :width="width"
      :height="height"
      viewBox="0 0 120 120"
    >
      <circle
        cx="60"
        cy="60"
        :r="radiusCircle"
        fill="none"
        :stroke="backgroundColor"
        :stroke-width="defaultOptions.layout.strokeWidth"
      />
      <circle
        cx="-60"
        cy="60"
        :r="radiusCircle"
        class="progress"
        fill="none"
        :stroke="progressColor"
        :stroke-width="defaultOptions.layout.strokeWidth"
        :stroke-dasharray="strokeCircle"
        :stroke-dashoffset="strokeCircleOffset"
      />
    </svg>
  </div>
</template>

<script>
import { ProgressBarMixin } from '../mixins/ProgressBarMixin'

export default {
  name: 'ProgressBarCircle',
  mixins: [ProgressBarMixin],
  props: {
    options: {
      type: Object,
      required: false,
      default: () => {}
    },
    value: {
      type: Number,
      required: false,
      default: 0
    }
  }
}
</script>

<style scoped>
.progress {
  transform: rotate(-90deg); 
}
</style>