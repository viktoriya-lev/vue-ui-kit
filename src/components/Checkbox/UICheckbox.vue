<template>
  <div :class="[{'switch-container': type === 'switch'}]">
    <input
      :id="id"
      :name="name"
      :value="value"
      :checked="checked"
      :disabled="disabled"
      type="checkbox"
      :class="[
        {'checkbox': type === 'checkbox'},
        {'switch': type === 'switch'}
      ]"
      @input="handleClick"
    >
    <label
      :for="id"
    >
      {{ label }}
    </label>
    <label
      v-if="type === 'switch'"
      :for="id"
      class="switch__label"
    >
      {{ label }}
    </label>
  </div>
</template>

<script setup>
const props = defineProps({
  id: {
    type: String,
    default: ''
  },
  name: {
    type: String,
    default: ''
  },
  value: {
    type: String,
    default: ''
  },
  label: {
    type: String,
    default: ''
  },
  checked: {
    type: Boolean,
    default: false
  },
  disabled: {
    type: Boolean,
    default: false
  },
  group: {
    type: Boolean,
    default: false
  },
  type: {
    type: String,
    default: 'checkbox'
  }
});

const emits = defineEmits(['update:checked', 'update-checkbox-group']);

const handleClick = (event) => {
  if (props.group) {
    emits('update-checkbox-group', { optionId: props.id, checked: event.target.checked })
  } else {
    emits('update:checked', event.target.checked);
  }
};
</script>

<style lang="scss">
.checkbox {
  position: absolute;
  opacity: 0;
  z-index: -1;

  & + label {
    display: inline-flex;
    align-items: center;
    user-select: none;
    cursor: pointer;
  }

  & + label::before {
    content: '';
    display: inline-block;
    width: 24px;
    height: 24px;
    flex-shrink: 0;
    flex-grow: 0;
    border: 1px solid #adb5bd;
    border-radius: 6px;
    margin-right: 10px;
    background-repeat: no-repeat;
    background-position: center center;
    background-size: 50% 50%;
  }

  &:checked + label::before {
    border-color: var(--color-primary);
    background-color: var(--color-primary);
    background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 8 8'%3e%3cpath fill='%23fff' d='M6.564.75l-3.59 3.612-1.538-1.55L0 4.26 2.974 7.25 8 2.193z'/%3e%3c/svg%3e");
  }

  &:not(:disabled):not(:checked) + label:hover::before {
    border-color: var(--color-primary-hover);
  }

  &:not(:disabled):active + label::before {
    background-color: var(--color-primary);
    border: 1px solid #ECEBED;
  }

  &:focus + label::before {
    box-shadow: var(--box-shadow_button);
  }

  &:focus:not(:checked) + label::before {
    border-color: var(--color-primary);
  }

  &:disabled + label::before {
    background-color: #e9ecef;
    border: 1px solid #ECEBED;
  }
}

.switch {
  position: absolute;
  width: 0;
  height: 0;
  opacity: 0;
  visibility: hidden;
  z-index: -1;

  &-container {
    display: flex;
    align-items: center;
  }

  &__label {
    margin-left: 10px;
  }

  & + label {
    display: block;
    width: 50px;
    height: 35px;
    border: 1px solid #adb5bd;
    border-radius: 100px;
    background: #fafafa;
    text-indent: -9999px;
    cursor: pointer;
    position: relative;

    &::after {
      content: "";
      position: absolute;
      top: 50%;
      left: 5px;
      width: 26px;
      height: 26px;
      background: var(--color-primary);
      border-radius: 90px;
      transition: 0.3s;
      transform: translateY(-50%);
    }
  }

  &:checked {
    & + label {
      background: var(--color-primary);

      &::after {
        background: var(--color-white);
        left: calc(100% - 5px);
        transform: translateX(-100%) translateY(-50%);
      }

      &:active::after {
        width: 33px;
      }
    }
  }
}
</style>
