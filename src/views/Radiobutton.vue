<template>
  <h1 class="heading-1">Radiobutton</h1>

  <h2 class="heading-2">Basic</h2>
  <div class="line line_block">
    <p>Your faculty: {{ selectedHogwartsFaculty }}</p>
    <div
      v-for="faculty in hogwartsFaculties"
      :key="faculty.id"
    >
      <UIRadiobutton
        :id="faculty.id"
        :value="faculty.name"
        :label="faculty.name"
        name="hogwartsFaculties"
        v-model:checkedValue="selectedHogwartsFaculty"
      />
    </div>
  </div>

  <h2 class="heading-2">Disabled</h2>
  <div class="line">
    <UIRadiobutton
      id="radioDisabled"
      value="Radio disabled"
      label="Radiobutton disabled"
      name="radioDisabled"
      :disabled="isDisabled"
      v-model:checkedValue="disabledRadioChecked"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import UIRadiobutton from "@/components/UIRadiobutton.vue";

const hogwartsFaculties = ref([
  { name: 'Gryffindor', id: '1' },
  { name: 'Slytherin', id: '2' },
  { name: 'Ravenclaw', id: '3' },
  { name: 'Hufflepuff', id: '4' },
]);

const selectedHogwartsFaculty = ref('');

const isDisabled = ref(true);
const disabledRadioChecked = ref(true);
</script>
