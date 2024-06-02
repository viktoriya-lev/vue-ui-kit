<template>
  <div class="progress-circle">
    <span
      class="progress-circle__percent"
      :style="[{'color': `var(--color-${color})`}]"
    >
      {{ percent }}%
    </span>
    <svg width="120" height="120" viewBox="0 0 120 120" class="progress-circle__svg">
      <circle
        cx="60"
        cy="60"
        r="54"
        fill="none"
        :stroke="`var(--color-${color}_hover)`"
        stroke-width="12" />
      <circle
        class="progress-circle__line"
        :style="[{'stroke-dashoffset': `calc(100 - ${percent})`}]"
        cx="60"
        cy="60"
        r="54"
        fill="none"
        :stroke="`var(--color-${color})`"
        stroke-width="12"
        pathLength="100" />
    </svg>
  </div>
</template>

<script setup>
defineProps({
  percent: {
    type: Number,
    required: true
  },
  color: {
    type: String,
    default: 'primary'
  }
})
</script>

<style lang="scss">
.progress-circle {
  position: relative;
  margin-bottom: 20px;
  width: 120px;
  height: 120px;

  &__svg {
    transform: rotate(-90deg);
  }

  &__percent {
    position: absolute;
    left: 0;
    width: 100%;
    top: 0;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: bold;
    font-size: 18px;
  }

  &__line {
    stroke-dasharray: 100;
    transition: .5s;
  }
}
</style>
