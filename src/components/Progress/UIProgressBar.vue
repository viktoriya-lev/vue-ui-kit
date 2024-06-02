<template>
  <div
    class="progress-bar__container"
    :style="[{'max-width': maxWidth}]"
  >
    <span
      class="progress-bar__percent"
      :style="[{'color': `var(--color-${color})`}]"
    >
      {{ percent }}%
    </span>
    <div
      class="progress-bar"
      :style="[{'background-color': `var(--color-${color}_hover)`}]"
    >
      <div
        :style="[
          {'width': `${percent}%`},
          {'background-color': `var(--color-${color})`}
        ]"
        class="progress-bar__bar"
      >

      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  maxWidth: {
    type: String,
    default: '300px'
  },
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
.progress-bar {
  height: 10px;
  border-radius: 4px;

  &__container {
    margin-bottom: 20px;
    overflow: hidden;
  }

  &__bar {
    height: 100%;
    border-radius: 4px;
    transition: .5s;
  }

  &__percent {
    display: block;
    text-align: center;
    font-weight: bold;
    font-size: 17px;
    margin-bottom: 10px;
  }
}
</style>
