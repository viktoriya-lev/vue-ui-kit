<template>
  <nav
    :class="[
      'sidebar',
      { 'is-open': openSidebar }
    ]"
  >
    <router-link
      v-for="link in links"
      :key="link.name"
      :to="link.href"
      class="sidebar__link"
    >
      {{ link.name }}
    </router-link>
  </nav>
</template>

<script setup>
import { ref } from 'vue';

defineProps({
  openSidebar: {
    type: Boolean,
    required: true
  }
})

const links = ref([
  { name: 'Typography', href: '/typography' },
  { name: 'Button', href: '/button' },
  { name: "Checkbox", href: "/checkbox" },
  { name: "Radiobutton", href: "/radiobutton" },
  { name: "Progress", href: "/progress" },
  { name: "Input", href: "/input" },
  // { name: "Tabs", href: "/tabs" },
  // { name: "Table", href: "/table" },
]);
</script>

<style lang="scss">
.sidebar {
  position: fixed;
  left: 0;
  top: 0;
  width: 250px;
  height: 100%;
  padding: 92px 20px 20px 40px;
  background-color: var(--color-white);
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.07);
  transform: translateX(-250px);
  transition: var(--transition);
  z-index: 99;

  &__link {
    display: block;
    margin-bottom: 10px;
    border: 2px solid var(--color-white);
    border-radius: 12px;
    font-weight: bold;
    transition: var(--transition);

    &:hover {
      color: var(--color-primary_hover);
    }
  }

  &.is-open {
    transform: translateX(0);
  }
}
</style>
