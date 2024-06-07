<template>
  <div class="tab-nav">
    <UIButton
      v-for="tab in names"
      :key="tab.name"
      color="warning"
      :text="tab.label"
      outlined
      :class="['tab-nav__item', { 'active': tab.name === activeTab }]"
      @click="clickOnTab(tab.name)"
    />
  </div>

  <div class="tab-content">
    <slot />
  </div>
</template>

<script setup>
import UIButton from '@/components/UIButton.vue';

defineProps({
  names: {
    type: Array,
    required: true
  },
  activeTab: {
    type: String,
    required: false
  }
});

const emit = defineEmits(['changeTab']);

const clickOnTab = (tabName) => {
  emit('changeTab', tabName)
}
</script>

<style scoped lang="scss">
.tab {
  &-nav {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 20px;

    &__item {
      font-size: 15px;

      &.active {
        background: var(--color-warning);
        color: var(--color-white);
      }
    }
  }

  &-content {
    padding: 20px;
    border-radius: 7px;
    background: var(--color-white);
  }
}
</style>
