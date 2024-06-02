<template>
  <h1 class="heading-1">Progress</h1>

  <h2 class="heading-2">Progress bar</h2>
  <div class="line line_block">
    <UIProgressBar
      maxWidth="400px"
      :percent="percentBar"
      color="success"
    />
    <UIButton
      text="Increase by 10%"
      color="success"
      outlined
      @click="increaseBar"
    />
  </div>

  <h2 class="heading-2">Progress circle</h2>
  <div class="line line_block">
    <UIProgressCircle
      :percent="percentCircle"
      color="secondary"
    />
    <UIButton
      text="Increase by 10%"
      color="secondary"
      outlined
      @click="increaseCircle"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import UIProgressBar from '@/components/Progress/UIProgressBar.vue';
import UIButton from "@/components/UIButton.vue";
import UIProgressCircle from "@/components/Progress/UIProgressCircle.vue";

const percentBar = ref(40);
const percentCircle = ref(60);

const increaseBar = () => {
  if (percentBar.value === 100) return;
  percentBar.value += 10;
};

const increaseCircle = () => {
  if (percentCircle.value === 100) return;
  percentCircle.value += 10;
}
</script>
