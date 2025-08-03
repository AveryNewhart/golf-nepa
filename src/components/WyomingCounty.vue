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
      id: 'emanon-country-club',
      name: 'Emanon Country Club',
      image: '/imgs/emanonLogo.jpeg',
      rating: '4.5/5',
      ratingLink: 'https://www.google.com/search?sca_esv=34fbce1b6673e2ad&sxsrf=AE3TifMgiVPuF8yfTVkuuka_qJ8KZNeQag:1754233058548&q=emanon+country+club&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s7kgIcgNoI2bV6pCNbcH8yvYeNEAMQDqeeqJWjxtLVa1Xse7VquKaMJWSpsXrX98EZrA5O87QJv8tCzmacaCIODbpq2TefUX7EomhxpyxdCprq9mmw%3D%3D&sa=X&sqi=2&ved=2ahUKEwivkLuy8-6OAxU-FFkFHbIZNVAQrrQLegQIIRAA',
      address: '543 Old State Rd, Falls, PA 18615',
      town: 'Falls',
      holes18: {
          weekday: {
          General: { cart: '$35', notes: 'Open-3pm' },
          Twilight: { cart: '$30', notes: 'After 3pm'  }
        },
        weekend: {
          General: { cart: '$45', notes: 'Open-3pm' },
          Twilight: { cart: '$40', notes: 'After 3pm'  }
        },
      },
      GeneralNotes: 'Driving Range | Semi-private Club',
      website: 'http://emanoncc.com/',
      phoneNumber: '(570) 388-6112',
      googlePlaceId: 'ChIJhSY0yI4kxYkRUBg-fm2sL5Q',
      courseLength: '5665 yards'
    },
    {
      id: 'shadowbrook-golf-course',
      name: 'Shawdowbrook Golf Course',
      image: '/imgs/shadowbrookLogo.png',
      rating: '3.9/5',
      ratingLink: 'https://www.google.com/search?sca_esv=34fbce1b6673e2ad&sxsrf=AE3TifPC9n-X-o1pZIF5rl3f04Z9WdUX6Q:1754233571490&q=shadowbrook+golf+course+tunkhannock+pa&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s_F5duWr7UjWPi8qLfK7fOtrd-zLMJWURnIKA_zp_JhO02S85cpin9d6jd1FbxOU6QfwDlpyZ_E9hlDQ-1SKCSpM-ICHktynnatI4nH3rfJnyh7Ijw%3D%3D&sa=X&ved=2ahUKEwi-xIan9e6OAxVyFlkFHaQtFGYQrrQLegQIGxAA',
      address: '201 Resort Ln, Tunkhannock, PA 18657',
      town: 'Tunkhannock',
      holes9: {
        weekday: {
          General: { walking: '$20', cart: '$28', notes: 'All Day' }
        },
        weekend: {
          General: { walking: '$26', cart: '$34', notes: 'All Day' },
        },
        senior: {
          weekday: { walking: '$18', cart: '$26', notes: 'After 10am' },
          weekend: { walking: '$24', cart: '$30', notes: 'After 2pm' }
        },
      },
      holes18: {
          weekday: {
          General: { walking: '$28', cart: '$38', notes: 'Open-3pm' },
          Twilight: { cart: '$28', notes: 'After 3pm'  }
        },
        weekend: {
          General: { walking: '$32', cart: '$46', notes: 'Open-3pm' },
          Twilight: { cart: '$36', notes: 'After 3pm'  }
        },
        senior: {
          weekday: { walking: '$24', cart: '$34', notes: 'All Day' },
          weekend: { walking: '$30', cart: '$42', notes: 'All Day' }
        },
        junior: {
          weekday: { walking: '$24', cart: '$44', notes: 'After 10am' },
          weekend: { walking: '$24', cart: '$44', notes: 'After 2pm' }
        },
      },
      GeneralNotes: 'Senior is 60+ | Junior is 16 & Under',
      website: 'https://shadowbrookresort.com/',
      phoneNumber: '(570) 836-2151',
      googlePlaceId: 'ChIJIzcdADwwxYkRbUk1_n3H0JY',
      courseLength: '6033 yards'
    },
    {
      id: 'stonehedge-golf-course',
      name: 'Stonehedge Golf Course',
      image: '/imgs/stonehedgeLogo.jpeg',
      rating: '4.8/5',
      ratingLink: 'https://www.google.com/search?sca_esv=34fbce1b6673e2ad&sxsrf=AE3TifPNco7ttDW__Px5AvZJRC6sk0wKCg:1754234434142&q=stonehedge+golf+course+pa&si=AMgyJEvkVjFQtirYNBhM3ZJIRTaSJ6PxY6y1_6WZHGInbzDnMaIqimUflZ13RmvSmgltow12lu4eLRhIAwMEu09g6HB1nkjq72XBqRRheyoamaZIzfKj6hnTLTZpNUVldBL5IFVyJehD5P1VSuwVJFYHsBJ0yVkQ0Q%3D%3D&sa=X&ved=2ahUKEwij4LLC-O6OAxUwGlkFHYs1CxEQrrQLegQIGhAA',
      address: '55 Stone Hedge Dr, Tunkhannock, PA 18657',
      town: 'Tunkhannock',
      holes9: {
        weekday: {
          General: { cart: '$25', notes: 'All Day' }
        },
        weekend: {
          General: { cart: '$30', notes: 'All Day' },
        },
      },
      holes18: {
          weekday: {
          General: { cart: '$40', notes: 'Open-1pm' },
          Twilight: { cart: '$35', notes: 'After 1pm'  }
        },
        weekend: {
          General: { cart: '$55', notes: 'Open-1pm' },
          Midday: { cart: '$45', notes: '1pm-3pm' },
          Twilight: { cart: '$40', notes: 'After 3pm'  }
        },
        senior: {
          weekday: { cart: '$32', notes: 'Also Ladies + Military' },
        },
      },
      GeneralNotes: 'Driving Range + Golf Simulator',
      website: 'https://www.playstonehedge.com/',
      phoneNumber: '(570) 836-5108',
      googlePlaceId: 'ChIJNSKAY7zVxIkRr3T6u9xgcsA',
      courseLength: '6489 yards'
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
  