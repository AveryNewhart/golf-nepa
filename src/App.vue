<script setup lang="ts">
import { ref } from 'vue';
import Nav from './components/Nav.vue';
import ThemeSelector from './components/ThemeSelector.vue';
import Footer from './components/Footer.vue';
// import BradfordCounty from './components/LancasterCounty.vue';
// import CarbonCounty from './components/YorkCounty.vue';
// import LackawannaCounty from './components/ChesterCounty.vue';
// import LuzerneCounty from './components/MontgomeryCounty.vue';
// import MonroeCounty from './components/BerksCounty.vue';
// import Pikeounty from './components/LebanonCounty.vue';
// import SchuylkillCounty from './components/DauphinCounty.vue';
// import SullivanCounty from './components/PhiladelphiaCounty.vue';
// import SusquehannaCounty from './components/LehighCounty.vue';
// import WayneCounty from './components/NorthamptonCounty.vue';
// import WyomingCounty from './components/DelawareCounty.vue';


// County view switcher 
type CountyView = 'lancaster' | 'york' | 'chester' | 'montgomery' | 'berks' | 'lebanon' | 'dauphin' | 'philadelphia' | 'lehigh' | 'northampton' | 'franklin';
const currentView = ref<CountyView>('lancaster');
</script>

<template>
  <div class="app-wrapper">
    <ThemeSelector/>
    <Nav @switch-view="(view: CountyView) => (currentView = view)" />

    <!-- <div class="content-wrapper">
      <div class="main-container">
        <LancasterCounty v-if="currentView === 'lancaster'" />
        <YorkCounty v-else-if="currentView === 'york'" />
        <ChesterCounty v-else-if="currentView === 'chester'" />
        <MontgomeryCounty v-else-if="currentView === 'montgomery'" />
        <BerksCounty v-else-if="currentView === 'berks'" />
        <LebanonCounty v-else-if="currentView === 'lebanon'" />
        <DauphinCounty v-else-if="currentView === 'dauphin'" />
        <PhiladelphiaCounty v-else-if="currentView === 'philadelphia'" />
        <LehighCounty v-else-if="currentView === 'lehigh'" />
        <NorthamptonCounty v-else-if="currentView === 'northampton'" />
        <FranklinCounty v-else />
      </div>
    </div> -->

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
