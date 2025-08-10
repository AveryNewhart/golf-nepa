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
      id: 'hidden-valley-golf-course',
      name: 'Hidden Valley Golf Course',
      image: '/imgs/hiddenValleyLogo.webp',
      rating: '4.3/5',
      ratingLink: 'https://www.google.com/search?sca_esv=9dcc5089927ade44&sxsrf=AE3TifMcwRdZCc_Z1VaMmNYrP2bMz1mbHA:1754769826856&q=hidden+valley+golf+course&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8swmDYdsTmJ08LmqNFbw0mSqkMreOOjLKJhq36wtxyA4f0sLRkqC5FADy9IYMccXlVCztgTgwUYQa5zzkkrrITPUZqzB8-Nj7O7RkJsV3w5UBH43CIg%3D%3D&sa=X&ved=2ahUKEwjC38SBw_6OAxVtLVkFHUZGNJwQrrQLegQIHBAA',
      address: '1753 Panther Valley Rd, Pine Grove, PA 17963',
      town: 'Pine Grove',
      holes9: {
        weekday: {
          General: { cart: '$35', notes: 'Open-3pm' },
          Twilight: { cart: '$35', notes: '3pm-Close' }
        },
        weekend: {
          General: { cart: '$35', notes: 'Open-3pm' },
          Twilight: { cart: '$35', notes: '3pm-Close' }
        },
      },
      holes18: {
        weekday: {
          Morning: { walking: '$31', cart: '$39', notes: 'Open-11am' },
          Midday: { walking: '$31', cart: '$34', notes: '11am-1pm' },
          General: { walking: '$31', cart: '$31', notes: '1pm-3pm' },
          Twilight: { walking: '$26', cart: '$29', notes: 'After 3pm' }
        },
        weekend: {
          Morning: { walking: '$39', cart: '$49', notes: 'Open-11am' },
          Midday: { walking: '$35', cart: '$43', notes: '11am-1pm' },
          General: { walking: '$35', cart: '$40', notes: '1pm-3pm' },
          Twilight: { walking: '$27', cart: '$32', notes: 'After 3pm' }
        },
        senior: {
          weekday: { walking: '$26', cart: '$31', notes: 'All Day' },
        },
        junior: {
          weekday: { cart: '$20', notes: '$2 Off After Noon' },
          weekend: { cart: '$20', notes: 'ONLY After Noon' }
        },
      },
      GeneralNotes: 'Senior is 60+ | Junior 15 & Under with paying adult | Active Military gets Senior rate',
      website: 'https://www.hidden.distinctgolf.com/',
      phoneNumber: '(570) 739-4455',
      googlePlaceId: 'ChIJEcqogav6xYkRrD0OhKoiAPU',
      courseLength: '6361 yards'
    },
    {
      id: 'mountain-valley-golf-course',
      name: 'Mountain Valley Golf Course',
      image: '/imgs/mtnValleyLogo.jpeg',
      rating: '4.5/5',
      ratingLink: 'https://www.google.com/search?sca_esv=d66f763f381654b2&sxsrf=AE3TifPR9vx2EqfYYmpru4Mga5lZC9xoeQ:1754772332809&q=mountain+valley+golf+course&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8szLRrBiNVEwseni0VyFJ1VtIo-q-asHYoc3uc30VDXjvNkrLepofQWSX8fmmB__A4fc0zazPy0CB_YIA4JYi7tZcHY8gQrGcyyhhYJVI0FynSJ8rYA%3D%3D&sa=X&ved=2ahUKEwjf9ruszP6OAxULEFkFHdxDMEAQrrQLegQIOBAA',
      address: '1021 Brockton Mountain Dr, Barnesville, PA 18214',
      town: 'Barnesville',
      holes9: {
        weekday: {
          General: { cart: '$28', notes: 'All Day' }
        },
        weekend: {
          General: { cart: '$45', notes: 'Open-2pm' },
          Twilight: { cart: '$35', notes: '2pm-Close' }
        },
      },
      holes18: {
          weekday: {
          General: { walking: '$25', cart: '$39', notes: 'Open-2pm' },
          Twilight: { walking: '$25', cart: '$33', notes: 'After 2pm'  }
        },
        weekend: {
          General: { cart: '$54', notes: 'Open-2pm' },
          Twilight: { walking: '$30', cart: '$42', notes: 'After 2pm'  }
        },
        senior: {
          weekday: { cart: '$33', notes: 'All Day' },
          weekend: { cart: '$54', notes: 'All Day' }
        },
      },
      GeneralNotes: '36 Holes | Monday Special $28 All Day | Junior Rates 50% Off Regular Rates | Senior is 55+',
      website: 'https://mtvalleygolf.com/',
      phoneNumber: '(570) 467-2242',
      googlePlaceId: 'ChIJ8x2eLAWVxYkR5dscyPpifm8',
      courseLength: '6739 yards'
    },
    {
      id: 'white-birch-golf-course',
      name: 'White Birch Golf Course',
      image: '/imgs/whiteBirchLogo.png',
      rating: '4.3/5',
      ratingLink: 'https://www.google.com/search?sca_esv=46b9746b866c6f5c&sxsrf=AE3TifNJSNoxJls7xfYKkFAaNm2obSUu6g:1754784391692&q=white+birch+golf+course&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s7tDuCZ0uPGMYC4DfE4YWiVP4S24TdO4ykgMaLBb8J-4MhYORc3yBCjck9X3D-iZTkLwhgLr0sbDAxMKiMP5PZAE8q6PWMCz96H2eavLDcFvlscEkS9CDnvhkwrLgi7EAPyyNEw%3D&sa=X&ved=2ahUKEwiO38ui-f6OAxWVFFkFHSEbKmcQrrQLegQIGhAA',
      address: '660 Tuscarora Park Rd, Barnesville, PA 18214',
      town: 'Barnesville',
      holes9: {
        weekday: {
          General: { walking: '$7', cart: '$12', notes: 'All Day' }
        },
        weekend: {
          General: { walking: '$12', cart: '$17', notes: 'Open-1pm' },
          Twilight: { walking: '$10', cart: '$15', notes: 'After 1pm' }
        },
      },
      holes18: {
        weekday: {
          General: { walking: '$10', cart: '$20', notes: 'All Day' },
        },
        weekend: {
          General: { walking: '$20', cart: '$30', notes: 'Open-1pm' },
          Twilight: { walking: '$15', cart: '$25', notes: 'After 1pm' }
        },

      },
      GeneralNotes: '18 Hole Main Course | 9 Hole Executive Course (call for availability Mon/Tue)',
      website: 'https://whitebirchgolf.com/',
      phoneNumber: '(570) 467-2525',
      googlePlaceId: 'ChIJJY3QA42-xYkRVIAWie1aTt4',
      courseLength: '5109 yards'
    },
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