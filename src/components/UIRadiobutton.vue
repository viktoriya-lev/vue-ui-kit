<template>
  <input
    :id="id"
    :name="name"
    :value="value"
    :checked="checked"
    :disabled="disabled"
    type="radio"
    class="radiobutton"
    @input="handleClick"
  >
  <label
    :for="id"
  >
    {{ label }}
  </label>
</template>

<script setup>
defineProps({
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
  }
});

const emit = defineEmits(['update:checked-value']);

const handleClick = (event) => {
  emit('update:checked-value', event.target.value);
};
</script>

<style lang="scss">
.radiobutton {
  position: absolute;
  z-index: -1;
  opacity: 0;

  & + label {
    display: inline-flex;
    align-items: center;
    user-select: none;
  }

  & + label::before {
    content: '';
    display: inline-block;
    flex-shrink: 0;
    flex-grow: 0;
    width: 24px;
    height: 24px;
    margin-right: 10px;
    border: 1px solid #adb5bd;
    border-radius: 50%;
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
    border-color: var(--color-primary_hover);
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
    background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 8 8'%3e%3cpath fill='%23fff' d='M6.564.75l-3.59 3.612-1.538-1.55L0 4.26 2.974 7.25 8 2.193z'/%3e%3c/svg%3e");
  }
}
</style>
