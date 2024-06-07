<template>
  <h1 class="heading-1">Tabs</h1>

  <UITabs
    :names="tabs"
    :activeTab="activeTab"
    @changeTab="changeTab"
  >
    <p v-if="activeTab === 'about'">
      Банальные, но неопровержимые выводы, а также предприниматели в сети интернет своевременно верифицированы. Есть над чем задуматься: представители современных социальных резервов рассмотрены исключительно в разрезе маркетинговых и финансовых предпосылок. Внезапно, интерактивные прототипы освещают чрезвычайно интересные особенности картины в целом, однако конкретные выводы, разумеется, объединены в целые кластеры себе подобных.
    </p>
    <p v-if="activeTab === 'Vue'">
      Vue.js — JavaScript-фреймворк с открытым исходным кодом для создания пользовательских интерфейсов. Легко интегрируется в проекты с использованием других JavaScript-библиотек. Может функционировать как веб-фреймворк для разработки одностраничных приложений в реактивном стиле.
    </p>
    <p v-if="activeTab === 'React'">
      React — JavaScript-библиотека с открытым исходным кодом для разработки пользовательских интерфейсов. React разрабатывается и поддерживается Facebook, Instagram и сообществом отдельных разработчиков и корпораций. React может использоваться для разработки одностраничных и мобильных приложений.
    </p>
  </UITabs>
</template>

<script setup>
import { ref } from 'vue';
import UITabs from "@/components/UITabs.vue";

const tabs = [
  { name: 'about', label: 'О проекте' },
  { name: 'Vue', label: 'Про Vue' },
  { name: 'React', label: 'Про React' },
];

const activeTab = ref('Vue');

const changeTab = (tabName) => {
  activeTab.value = tabName;
}
</script>

<style scoped lang="scss">

</style>
