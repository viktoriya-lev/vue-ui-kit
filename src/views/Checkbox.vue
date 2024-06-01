<template>
  <h1 class="heading-1">Checkbox</h1>

  <h2 class="heading-2">Checkbox active</h2>
  <div class="line">
    <UICheckbox
      v-model:checked="isActive"
      id="checkboxActive"
      label="Checkbox Active"
      name="checkboxActive"
      value="I like it"
    />
  </div>

  <h2 class="heading-2">Checkbox disabled</h2>
  <div class="line">
    <UICheckbox
      v-model:checked="checkboxDisabledChecked"
      id="checkboxDisabled"
      label="Checkbox Disabled"
      name="checkboxDisabled"
      value="I like it"
      :disabled="isDisabled"
    />
  </div>

  <h2 class="heading-2">Checkbox Group</h2>
  <div class="line_block">
    <p>Selected coffee: {{ selectedCoffee }}</p>
    <UICheckboxGroup
      v-model:value="selectedCoffee"
      :options="coffeeList"
      name="coffee"
    />
  </div>

  <h2 class="heading-2">Switch</h2>
  <div class="line">
    <UICheckbox
      v-model:checked="isSwitchActive"
      id="switch"
      label="A am a switch"
      name="switch"
      value="I like it"
      type="switch"
    />
  </div>
</template>

<script setup>
import UICheckbox from '@/components/Checkbox/UICheckbox.vue';
import { ref } from 'vue';
import UICheckboxGroup from "@/components/Checkbox/UICheckboxGroup.vue";

const isSwitchActive = ref(false);
const isActive = ref(true);
const isDisabled = ref(true);
const checkboxDisabledChecked = ref(true);

const coffeeList = ref([
  { name: 'Cappuccino', id: '1' },
  { name: 'Latte', id: '2' },
  { name: 'Raf', id: '3' },
  { name: 'Espresso', id: '4' },
  { name: 'Americano', id: '5' },
]);

const selectedCoffee = ref(['1', '3']);
</script>
