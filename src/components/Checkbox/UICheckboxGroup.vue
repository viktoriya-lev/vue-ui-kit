<template>
  <div
    v-for="option in options"
    :key="option.id"
  >
    <UICheckbox
      :id="option.id"
      :label="option.name"
      :value="option.name"
      :name="name"
      :checked="value.includes(option.id)"
      group
      @updateCheckboxGroup="handleUpdate"
    />
  </div>
</template>

<script setup>
import UICheckbox from '@/components/Checkbox/UICheckbox.vue';

const props = defineProps({
  value: {
    type: Array,
    required: false
  },
  name: {
    type: String,
    required: true
  },
  options: {
    type: Array,
    required: true,
    validator: (value) => {
      const hasNameKey = value.every((option) => Object.keys(option).includes('name'));
      const hasIdKey = value.every((option) => Object.keys(option).includes('id'));
      return hasNameKey && hasIdKey;
    }
  }
});

const emit = defineEmits(['update:value']);

const handleUpdate = (params) => {
  let updatedValue = [...props.value];

  if (params.checked) {
    updatedValue.push(params.optionId);
  } else {
    updatedValue.splice(updatedValue.indexOf(params.optionId), 1)
  }

  emit('update:value', updatedValue);
}
</script>

<style lang="scss">

</style>
