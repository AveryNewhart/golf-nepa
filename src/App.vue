<script setup lang="ts">
import { ref } from 'vue';
import Nav from './components/Nav.vue';
import ThemeSelector from './components/ThemeSelector.vue';
import Footer from './components/Footer.vue';
import BradfordCounty from './components/BradfordCounty.vue';
import CarbonCounty from './components/CarbonCounty.vue';
import LackawannaCounty from './components/LackawannaCounty.vue';
import LuzerneCounty from './components/LuzerneCounty.vue';
import MonroeCounty from './components/MonroeCounty.vue';
import PikeCounty from './components/PikeCounty.vue';
import SchuylkillCounty from './components/SchuylkillCounty.vue';
import SullivanCounty from './components/SullivanCounty.vue';
import SusquehannaCounty from './components/SusquehannaCounty.vue';
import WayneCounty from './components/WayneCounty.vue';
import WyomingCounty from './components/WyomingCounty.vue';

// County view switcher 
type CountyView = 'wyoming' | 'carbon' | 'lackawanna' | 'luzerne' | 'monroe' | 'pike' | 'schuylkill' | 'sullivan' | 'susquehanna' | 'wayne' | 'bradford';
const currentView = ref<CountyView>('wyoming');
</script>

<template>
  <div class="app-wrapper">
    <ThemeSelector/>
    <Nav @switch-view="(view: CountyView) => (currentView = view)" />

    <div class="content-wrapper">
      <div class="main-container">
        <WyomingCounty v-if="currentView === 'wyoming'" />
        <CarbonCounty v-else-if="currentView === 'carbon'" />
        <LackawannaCounty v-else-if="currentView === 'lackawanna'" />
        <LuzerneCounty v-else-if="currentView === 'luzerne'" />
        <MonroeCounty v-else-if="currentView === 'monroe'" />
        <PikeCounty v-else-if="currentView === 'pike'" />
        <SchuylkillCounty v-else-if="currentView === 'schuylkill'" />
        <SullivanCounty v-else-if="currentView === 'sullivan'" />
        <SusquehannaCounty v-else-if="currentView === 'susquehanna'" />
        <WayneCounty v-else-if="currentView === 'wayne'" />
        <BradfordCounty v-else />
      </div>
    </div>

    <Footer />
  </div>
</template>

<style scoped>
.app-wrapper {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.content-wrapper {
  flex: 1;
  display: flex;
  flex-direction: column;
}

.main-container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 2rem 1rem;
  width: 100%;
  flex: 1;
}
</style>
