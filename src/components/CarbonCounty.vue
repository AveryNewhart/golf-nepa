<script setup lang="ts">
import { useCourseUtilities, type Course } from '../composables/useCourseUtilities';
import CourseCardTemplate from './CourseCardTemplate.vue';
import '../assets/styles/course-cards.css';

// Use the shared utilities
const { 
  expandedCourses,
  isTimeBasedRates,
  isTimeSlotRate,
  getBackgroundColor,
  toggleDetails,
  getMapsLink,
  formatPhoneNumber 
} = useCourseUtilities();
  
  // Course data
  const courses: Course[] = [
    {
      id: 'blue-shamrock-golf-club',
      name: 'Blue Shamrock Golf Club',
      image: '/imgs/blueShamrockLogo.webp',
      rating: '4.1/5',
      ratingLink: 'https://www.google.com/search?sca_esv=1b131cb33424c794&sxsrf=AE3TifPdsKiechoMK-TUMwnWDd2_8W3tRA:1754530429759&q=blue+shamrock+golf+club&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s7gX4-isSGy3xhvBpdS-6Yh0w1CJHvkj6EiPTuwjw12HfogGM_P3I8q8CFNW6SsxHhQ8xH80i-Cpgp-tYYJkdSg1692lUvmDQHFa8uOLoKsULofAYw%3D%3D&sa=X&ved=2ahUKEwjzo42Yx_eOAxX_F1kFHYlYFG4QrrQLegQINxAA',
      address: '2230 Fireline Rd, Palmerton, PA 18071',
      town: 'Palmerton',
      holes9: {
        weekday: {
            General: { cart: '$28', notes: 'After Noon Only' }
        },
        weekend: {
            General: { cart: '$30', notes: 'After 2pm Only' }
        },
      },
      holes18: {
        weekday: {
          Morning: { cart: '$48', notes: 'Open-11:30am' },
          Midday: { cart: '$43', notes: '11:31am-2:30pm' },
          Twilight: { cart: '$39', notes: '2:31pm-Close' }
        },
        weekend: {
          Morning: { cart: '$63', notes: 'Open-11:30am' },
          Midday: { cart: '$53', notes: '11:31am-2:30pm' },
          Twilight: { cart: '$45', notes: '2:31pm-Close' }
        },
        senior: {
          weekday: { cart: '$43', notes: 'Mon-Thur' },
        },
      },
      website: 'https://golfblueshamrock.com/',
      phoneNumber: '(610) 826-2504',
      googlePlaceId: 'ChIJMY6v2IFOxIkR4bxnqb7rOZ8',
      courseLength: '6600 yards'
    },
    {
      id: 'split-rock-golf-course',
      name: 'Split Rock Golf Course',
      image: '/imgs/splitRockLogo.png',
      rating: '4.2/5',
      ratingLink: 'https://www.google.com/search?sca_esv=dc314041ceafd262&sxsrf=AE3TifN4w6yIh2UI3LyA9P1w7tiWWIOIUg:1754760280576&q=split+rock+country+club&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s7qkwqzn4CVdGo7C2Fkbe7uHVmDmfEsawhhfd6liw7JM2UzEtzprZRs3T4dpFRFtccarVg0Ta3O_rcdK_bdiHEnFq1SrRoCZWrB6o9Ys5AY7vXJh9femaGIO2mBWMQpOGU95N4mnaye49HPS9rwrxGYnaMM_&sa=X&ved=2ahUKEwj6gsK5n_6OAxX8GFkFHYoZAm4QrrQLegQIHBAA',
      address: '140 Wolf Hollow Rd, Lake Harmony, PA 18624',
      town: 'Lake Harmony',
      holes9: {
        weekday: {
          General: { walking: '$15', cart: '$40', notes: 'Open-2pm' },
          Twilight: { walking: '$15', cart: '$30', notes: 'After 2pm'  }
        },
        weekend: {
          General: { walking: '$25', cart: '$45', notes: 'Open-2pm' },
          Twilight: { walking: '$25', cart: '$40', notes: 'After 2pm'  }
        },
      },
      holes18: {
        weekday: {
          General: { cart: '$55', notes: 'Open-2pm' },
          Twilight: { cart: '$45', notes: 'After 2pm'  }
        },
        weekend: {
          General: { cart: '$85', notes: 'Open-2pm' },
          Twilight: { cart: '$75', notes: 'After 2pm'  }
        },
        senior: {
          weekday: { cart: '$45', notes: 'All Day' },
          weekend: { cart: '$70', notes: 'All Day' },
        },
        junior: {
          weekday: { cart: '$45', notes: 'All Day' },
          weekend: { cart: '$70', notes: 'All Day' },
        },
      },
      GeneralNotes: 'Senior 65+ | Junior 16 & Under | 2 Courses | Has Footgolf | Golf Simulators',
      website: 'https://www.golfsplitrock.com/',
      phoneNumber: '(570) 722-9901',
      googlePlaceId: 'ChIJsYWw6Db5xIkR4Ysk-MWuRUY',
      courseLength: '6807 yards'
    }
  ];
  
  
  </script>
  
  <template>
    <CourseCardTemplate
      :courses="courses"
      :expanded-courses="expandedCourses"
      :is-time-based-rates="isTimeBasedRates"
      :is-time-slot-rate="isTimeSlotRate"
      :get-background-color="getBackgroundColor"
      :toggle-details="toggleDetails"
      :get-maps-link="getMapsLink"
      :format-phone-number="formatPhoneNumber"
    />
  </template>
  
<style scoped>
</style>