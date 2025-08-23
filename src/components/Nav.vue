<script setup lang="ts">
import { ref, onMounted, watch } from 'vue'
// @ts-ignore
import imageMapResize from 'image-map-resizer'

// Define the type for the new list of counties
type CountyView = 'bradford' | 'susquehanna' | 'wayne' | 'sullivan' | 'wyoming' | 'lackawanna' | 'pike' | 'luzerne' | 'monroe' | 'carbon' | 'schuylkill';

const emit = defineEmits<{
  (e: 'switch-view', view: CountyView): void
}>()

// Set the initial view to the first county in your list
const currentView = ref<CountyView>('wyoming')
const fading = ref(false)
const showMap = ref(true)

const setView = (view: CountyView) => {
  if (currentView.value !== view) {
    fading.value = true
    setTimeout(() => {
      currentView.value = view
      emit('switch-view', view)
      fading.value = false
      showMap.value = false // This will hide the map and show the 'View Map' button
    }, 300)
  }
}

const openMap = () => {
  showMap.value = true
}

// Ensure the image map is responsive
onMounted(() => {
  imageMapResize()
})

watch(showMap, (visible) => {
  if (visible) {
    setTimeout(() => {
      imageMapResize()
    }, 0)
  }
})
</script>

<template>
  <nav>
    <div class="mx-auto p-5">
      <h1
        class="text-center text-white text-3xl font-semibold mb-6 transition-opacity duration-300"
        :class="{ 'opacity-0': fading, 'opacity-100': !fading }"
      >
        Public Golf Courses In {{
          currentView === 'wyoming' ? 'Wyoming' :
          currentView === 'bradford' ? 'Bradford' :
          currentView === 'susquehanna' ? 'Susquehanna' :
          currentView === 'wayne' ? 'Wayne' :
          currentView === 'sullivan' ? 'Sullivan' :
          currentView === 'lackawanna' ? 'Lackawanna' :
          currentView === 'pike' ? 'Pike' :
          currentView === 'luzerne' ? 'Luzerne' :
          currentView === 'monroe' ? 'Monroe' :
          currentView === 'carbon' ? 'Carbon' : 'Schuylkill'
        }} County
      </h1>

      <div class="county-map-container relative">
        <template v-if="showMap">
          <img
            src="/imgs/NepaBlackBordersFinal.png"
            usemap="#image-map"
            alt="NEPA County Map"
            class="w-full max-w-4xl mx-auto rounded-lg" />
          <p class="text-white text-md mt-2 mb-4 italic">
            Click a county to view their public golf courses
          </p>
          <map name="image-map">
            <area @click="setView('wyoming')" alt="WyomingCounty" title="WyomingCounty" coords="355,274,313,329,293,411,395,411,478,389,493,367,494,343,491,325,518,276" shape="poly">
            <area @click="setView('bradford')" alt="BradfordCounty" title="BradfordCounty" coords="26,80,37,289,297,319,338,261,322,80" shape="poly">
            <area @click="setView('susquehanna')" alt="SusquehannaCounty" title="SusquehannaCounty" coords="343,82,355,257,645,257,634,74" shape="poly">
            <area @click="setView('wayne')" alt="WayneCounty" title="WayneCounty" coords="651,70,679,471,705,472,820,271,786,159" shape="poly">
            <area @click="setView('sullivan')" alt="SullivanCounty" title="SullivanCounty" coords="65,315,84,395,155,449,213,461,253,449,267,448,294,338" shape="poly">
            <area @click="setView('lackawanna')" alt="LackawannaCounty" title="LackawannaCounty" coords="536,274,510,328,515,351,513,365,495,392,507,407,545,428,562,444,572,472,576,493,576,520,591,529,659,469,648,277" shape="poly">
            <area @click="setView('pike')" alt="PikeCounty" title="PikeCounty" coords="917,467,929,427,977,394,941,376,821,320,736,466,823,463,813,517,864,549,903,516" shape="poly">
            <area @click="setView('luzerne')" alt="LuzerneCounty" title="LuzerneCounty" coords="290,435,283,513,327,640,414,661,515,608,507,578,562,541,552,466,480,410" shape="poly">
            <area @click="setView('monroe')" alt="MonroeCounty" title="MonroeCounty" coords="851,565,789,529,798,482,649,497,590,562,650,625,626,650,626,655,626,650,660,713,729,675,811,625,847,580" shape-="poly">
            <area @click="setView('carbon')" alt="CarbonCounty" title="CarbonCounty" coords="430,670,537,761,575,740,644,718,606,659,602,650,626,632,590,585,560,563,555,601,505,638,571,595,545,567,532,616" shape="poly">
            <area @click="setView('schuylkill')" alt="SchuylkillCounty" title="SchuylkillCounty" coords="131,820,238,902,267,909,408,860,413,839,518,775,414,676,325,657,301,693,294,737" shape="poly">
          </map>
        </template>

        <template v-else>
          <button
            class="mt-6 px-6 py-3 bg-green-700 text-white rounded hover:bg-green-800 transition"
            @click="openMap"
          >
            View Map
          </button>
        </template>
      </div>
    </div>
  </nav>
</template>

<style scoped>
nav {
  /* background-color: var(--color-nav-bg); You can set your desired background color here */
  border-bottom: 2px solid white;
}
.county-map-container {
  text-align: center;
}
/* Makes the clickable areas show a pointer on hover */
area {
  cursor: pointer;
}
</style>