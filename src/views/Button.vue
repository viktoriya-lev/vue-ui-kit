<template>
  <h1 class="heading-1">Button</h1>

  <h2 class="heading-2">Disabled</h2>
  <div class="line">
    <UIButton
      text="Primary"
      color="primary"
      disabled
    />
    <UIButton
      text="Secondary"
      color="secondary"
      disabled
    />
  </div>

  <h2 class="heading-2">Colors</h2>
  <div class="line">
    <UIButton
      text="Primary"
      color="primary"
    />
    <UIButton
      text="Secondary"
      color="secondary"
    />
    <UIButton
      text="Success"
      color="success"
    />
    <UIButton
      text="Info"
      color="info"
    />
    <UIButton
      text="Warning"
      color="warning"
    />
    <UIButton
      text="Danger"
      color="danger"
    />
  </div>

  <h2 class="heading-2">Rounded</h2>
  <div class="line">
    <UIButton
      text="Primary"
      color="primary"
      rounded
    />
    <UIButton
      text="Secondary"
      color="secondary"
      rounded
    />
    <UIButton
      text="Success"
      color="success"
      rounded
    />
    <UIButton
      text="Info"
      color="info"
      rounded
    />
    <UIButton
      text="Warning"
      color="warning"
      rounded
    />
    <UIButton
      text="Danger"
      color="danger"
      rounded
    />
  </div>

  <h2 class="heading-2">Outlined</h2>
  <div class="line">
    <UIButton
      text="Primary"
      color="primary"
      outlined
    />
    <UIButton
      text="Secondary"
      color="secondary"
      outlined
    />
    <UIButton
      text="Success"
      color="success"
      outlined
    />
    <UIButton
      text="Info"
      color="info"
      outlined
    />
    <UIButton
      text="Warning"
      color="warning"
      outlined
    />
    <UIButton
      text="Danger"
      color="danger"
      outlined
    />
  </div>

  <h2 class="heading-2">Icon</h2>
  <div class="line">
    <UIButton
      icon="heart"
      color="primary"
      outlined
    />
    <UIButton
      icon="hand"
      color="secondary"
    />
    <UIButton
      icon="address-book"
      color="success"
      outlined
    />
    <UIButton
      icon="credit-card"
      color="info"
    />
    <UIButton
      icon="lemon"
      color="warning"
      outlined
    />
    <UIButton
      icon="hourglass"
      color="danger"
    />
  </div>

  <h2 class="heading-2">Size</h2>
  <div class="line">
    <UIButton
      text="Normal"
      color="primary"
    />
    <UIButton
      text="Large"
      color="primary"
      size="large"
    />
  </div>

  <h2 class="heading-2">Event</h2>
  <div class="line">
    <UIButton
      text="@click"
      color="danger"
      @click="eventForButton"
    />
  </div>
</template>

<script setup>
import UIButton from '@/components/UIButton.vue';

const eventForButton = () => {
  alert('You clicked danger button!')
}
</script>
