<template>
  <div class="container">
    <div
      class="sidebar__toggle"
      @click="toggleSidebar"
    >
      &#5125;
    </div>

    <Header />
    <Sidebar :openSidebar="isSidebarOpen" />

    <div :class="[
      'content',
      { 'content_full': !isSidebarOpen },
    ]"
    >
      <router-view />
    </div>
  </div>
</template>

<script setup>
import Header from '@/components/layout/Header.vue';
import Sidebar from '@/components/layout/Sidebar.vue';

import { ref } from 'vue';

const isSidebarOpen = ref(false);

const toggleSidebar = () => {
  isSidebarOpen.value = !isSidebarOpen.value;
};
</script>

<style lang="scss">
@import "./css/global.scss";

.content {
  max-width: 1400px;
  margin: 0 auto 0 250px;
  padding: 30px 60px;
  transition: var(--transition);

  &_full {
    margin-left: 0;
  }
}

.sidebar__toggle {
  position: fixed;
  left: 0;
  top: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 15px;
  height: 100%;
  padding-top: 92px;
  color: #fff;
  background-color: var(--color-primary);
  cursor: pointer;
  z-index: 1;
}

@media screen and (max-width: 1023px) {
  .content {
    margin-left: 0;
  }
}
</style>
