<template>
  <button
    :class="[
      'btn',
      `btn_${color}`,
      { 'btn_rounded': rounded },
      { 'btn_outlined': outlined },
      { 'btn_icon': icon },
      { 'btn_large': size === 'large' },
    ]"
    :disabled="disabled"
    @click="clickOnBtn"
  >
    <span v-if="icon">
      <font-awesome-icon :icon="`fa-regular fa-${icon}`" />
    </span>
    <span v-else>
      {{ text }}
    </span>
  </button>
</template>

<script setup>
defineProps({
  text: {
    type: String,
    default: 'Button'
  },
  color: {
    type: String,
    default: 'primary'
  },
  disabled: {
    type: Boolean,
    required: false
  },
  rounded: {
    type: Boolean,
    required: false
  },
  outlined: {
    type: Boolean,
    required: false
  },
  icon: {
    type: String,
    required: false
  },
  size: {
    type: String,
    default: 'normal'
  }
});

const emit = defineEmits(['click']);

const clickOnBtn = () => {
  emit('click');
}
</script>

<style lang="scss">
.btn {
  border-radius: 7px;
  padding: 12px 20px;

  &_primary {
    background-color: var(--color-primary);
    border: 1px solid var(--color-primary);

    &:enabled:hover {
      background-color: var(--color-primary_hover);
    }
  }

  &_secondary {
    background-color: var(--color-secondary);
    border: 1px solid var(--color-secondary);

    &:enabled:hover {
      background-color: var(--color-secondary_hover);
    }
  }

  &_success {
    background-color: var(--color-success);
    border: 1px solid var(--color-success);

    &:enabled:hover {
      background-color: var(--color-success_hover);
    }
  }

  &_info {
    background-color: var(--color-info);
    border: 1px solid var(--color-info);

    &:enabled:hover {
      background-color: var(--color-info_hover);
    }
  }

  &_warning {
    background-color: var(--color-warning);
    border: 1px solid var(--color-warning);

    &:enabled:hover {
      background-color: var(--color-warning_hover);
    }
  }

  &_danger {
    background-color: var(--color-danger);
    border: 1px solid var(--color-danger);

    &:enabled:hover {
      background-color: var(--color-danger_hover);
    }
  }

  &:disabled {
    opacity: .6;
    cursor: default;
  }

  &_rounded {
    border-radius: 15px;
  }

  &_outlined {
    background-color: transparent;
    color: var(--color-black);

    &:hover {
      color: var(--color-white);
    }
  }

  &_icon {
    width: 40px;
    height: 40px;
    padding: 0;
    border-radius: 50%;
  }

  &_large {
    padding: 16px 30px;
  }
}
</style>
