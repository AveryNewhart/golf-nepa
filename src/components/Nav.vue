<script setup lang="ts">
import { ref, onMounted, watch, computed } from 'vue'
import imageMapResize from 'image-map-resizer'

// Explicitly define the types for the emitted event to match App.vue
type CountyView = 'wyoming' | 'carbon' | 'lackawanna' | 'luzerne' | 'monroe' | 'pike' | 'schuylkill' | 'sullivan' | 'susquehanna' | 'wayne' | 'bradford';
const emit = defineEmits<{
  (e: 'switch-view', view: CountyView): void
}>()

// State to control map visibility
const showMap = ref(true)

const counties = [
  { name: 'Wyoming', coords: '276,216,245,259,230,326,376,303,388,282,382,263,402,216' },
  { name: 'Bradford', coords: '20,60,29,229,237,252,268,209,254,61' },
  { name: 'Susquehanna', coords: '264,62,277,203,507,204,498,58' },
  { name: 'Wayne', coords: '508,57,529,363,527,375,538,374,556,371,564,344,648,219,636,177,626,152,615,128,611,115,574,103,546,59' },
  { name: 'Sullivan', coords: '49,244,68,310,122,353,170,362,198,352,210,350,232,264' },
  { name: 'Lackawanna', coords: '506,216,517,365,485,389,479,396,464,412,452,410,449,363,438,345,421,333,391,317,392,298,402,278,401,254,409,237,418,217' },
  { name: 'Pike', coords: '653,229,583,340,571,368,603,364,624,363,641,360,631,404,666,427,681,425,694,416,701,400,714,381,719,350,757,307,743,288,706,285,694,280,682,274' },
  { name: 'Luzerne', coords: '227,338,218,397,258,499,322,515,408,475,396,456,399,446,422,429,450,424,440,408,435,379,428,362,416,346,374,323' },
  { name: 'Monroe', coords: '665,443,518,554,490,512,505,498,504,486,459,436,508,388,533,386,552,385,568,381,586,382,626,375,618,413,668,447,516,555' },
  { name: 'Carbon', coords: '337,525,418,595,444,583,456,579,475,569,501,560,476,517,469,509,489,493,476,479,462,464,440,440,420,451,424,478' },
  { name: 'Schuylkill', coords: '206,706,185,700,99,641,227,574,229,546,253,514,318,527,359,566,407,603,371,626,333,643,316,673,273,692' },
]

const currentView = ref('Wyoming')
const fading = ref(false)

const setView = (view: string) => {
  if (currentView.value !== view) {
    fading.value = true
    setTimeout(() => {
      currentView.value = view
      // The `view.toLowerCase()` call ensures we emit a string that matches our CountyView type
      emit('switch-view', view.toLowerCase() as CountyView)
      fading.value = false
      showMap.value = false // This is the new line to hide the map
    }, 300)
  }
}

const currentCountyName = computed(() => {
  const county = counties.find(c => c.name === currentView.value);
  return county ? county.name : 'Unknown';
});

// Watch for changes to `showMap` and re-initialize the image map resizer
watch(showMap, (visible) => {
  if (visible) {
    setTimeout(() => {
      imageMapResize()
    }, 0)
  }
})

onMounted(() => {
  imageMapResize()
})

</script>

<template>
  <nav>
    <div class="mx-auto p-5">
      <h1
        class="text-center text-white text-3xl font-semibold mb-6 transition-opacity duration-300"
        :class="{ 'opacity-0': fading, 'opacity-100': !fading }"
      >
        Public Golf Courses In {{ currentCountyName }} County
      </h1>

      <!-- Use v-if to conditionally show the map container -->
      <div v-if="showMap" class="county-map-container relative">
        <img
          src="/imgs/nepaSmaller.png"
          usemap="#image-map"
          alt="NEPA County Map"
          class="mx-auto rounded-lg transition-filter duration-300"
          :style="{ filter: `var(--map-filter, '')` }"
        />
        <p class="text-white text-md mt-2 mb-4 italic">
          Click a county to view their public golf courses
        </p>
        <map name="image-map">
          <area
            v-for="county in counties"
            :key="county.name"
            @click="setView(county.name)"
            :alt="county.name + 'County'"
            :title="county.name + 'County'"
            :coords="county.coords"
            shape="poly"
          >
        </map>
      </div>

      <!-- Show a link to bring the map back when it's hidden -->
      <div v-else class="text-center">
        <button 
          @click="showMap = true" 
          class="mt-6 px-6 py-3 bg-green-700 text-white rounded hover:bg-green-800 transition"
        >
          Show the map again
        </button>
      </div>
    </div>
  </nav>
</template>

<style scoped>
nav {
  background-color: var(--color-nav-bg); 
  border-bottom: 2px solid white;
}
.county-map-container {
  text-align: center;
}
area {
  cursor: pointer;
}
</style>
