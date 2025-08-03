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
      id: 'cricket-hill-golf-club',
      name: 'Cricket Hill Golf Club',
      image: '/imgs/cricketHillLogo.jpeg',
      rating: '4.5/5',
      ratingLink: 'https://www.google.com/search?sca_esv=41771b6d1dd3ed98&sxsrf=AE3TifM65q0bmmI4_jHa93IFkxkR3PZv1w:1754245516462&q=cricket+hill+golf+club&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s_bzGXV1BUqmeoGPV6is_ABmJecl1P50SwMLiurB8hWqL6vzGAMw-EQdM5aOQmqhqV6w2yvpyCJI__yPF8R_0Eg63fmGvy-ivFQru4LmMrtFjPmE_g%3D%3D&sa=X&ved=2ahUKEwiH7u3moe-OAxWbF1kFHbmTFQ4QrrQLegQIIBAA',
      address: '176 Cricket Hill Rd, Hawley, PA 18428',
      town: 'Hawley',
      holes9: {
        weekday: {
          General: { walking: '$12', cart: '$20', notes: 'All Day' }
        },
        weekend: {
          General: { walking: '$12', cart: '$22', notes: 'All Day' },
        },
        senior: {
          weekday: { cart: '$18', notes: 'Mon & Wed' },
        },
      },
      holes18: {
          weekday: {
            General: { walking: '$22', cart: '$34', notes: 'All Day' },
        },
        weekend: {
            General: { walking: '$22', cart: '$40', notes: 'All Day' },
        },
      },
      website: 'https://www.crickethillgc.com/',
      phoneNumber: '(570) 226-4366',
      googlePlaceId: 'ChIJVbMSh32yxIkRhxC-ro0jFTA',
      courseLength: '5800 yards'
    },
    {
      id: 'the-country-club-at-woodloch-springs',
      name: 'The Country Club At Woodloch Springs',
      image: '/imgs/woodlochSpringsLogo.png',
      rating: '4.7/5',
      ratingLink: 'https://www.google.com/search?sca_esv=41771b6d1dd3ed98&sxsrf=AE3TifOfyC6hvroc1aIEVhgt1KI3mbOg-g:1754248052667&q=the+country+club+at+woodloch+springs&si=AMgyJEvkVjFQtirYNBhM3ZJIRTaSJ6PxY6y1_6WZHGInbzDnMaOXxAC9U8h579oqorsMVKTWzt9h4HusP9I-DC2FtcQt-dgoyKYusFB6RQFzYm2gnuS9SZAfeWg-YYsaqlUH41KLP0cfrV8ThCGr7LR9pqZZqkmIzvK4BE24gxS0gQiIsfdmI7E%3D&sa=X&ved=2ahUKEwjRyJugq--OAxUnFFkFHewTHcIQrrQLegQIRxAA',
      address: '2 Woodloch Springs, Hawley, PA 18428',
      town: 'Hawley',
      holes9: {
        weekday: {
            General: { cart: '$60', notes: 'Open-2pm' },
            Twilight: { cart: '$55', notes: '2pm-Close' }
        },
        weekend: {
            General: { cart: '$70', notes: 'Open-2pm' },
            Twilight: { cart: '$60', notes: '2pm-Close' }
        },
      },
      holes18: {
        weekday: {
            General: { cart: '$100', notes: 'Open-2pm' },
            Twilight: { cart: '$80', notes: '2pm-Close' }
        },
        weekend: {
            General: { cart: '$130', notes: 'Open-2pm' },
            Twilight: { cart: '$100', notes: '2pm-Close' }
        },
      },
      website: 'https://www.woodloch.com/golf-spa/golf/',
      phoneNumber: '(570) 685-8102',
      googlePlaceId: 'ChIJEU9k94CuxIkRWSsxdV-dWhg',
      courseLength: '6579 yards'
    },
    {
      id: 'memorial-links-golf-course',
      name: 'Memorial Links Golf Course',
      image: '/imgs/memorialLinksLogo.jpeg',
      rating: '4.8/5',
      ratingLink: 'https://www.google.com/search?sca_esv=41771b6d1dd3ed98&sxsrf=AE3TifO8T2sUJc82DqSYHVfJtjdvV9B-kw:1754246755427&q=memorial+links+golf+course&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8sz-nl6hG3wx4xr3bHs39-7i8ctXuZTsonZyaeX4lURasY_YaChfpm3MIGI0L_uqVtYqwMI2j_ivmxpuBRx_GAKbEolNP6UHissiYhijlD4WEqiobFQ%3D%3D&sa=X&ved=2ahUKEwiqqdK1pu-OAxWgGlkFHSZYEcMQrrQLegQIIBAA',
      address: '106 Memorial Links Rd, Waymart, PA 18472',
      town: 'Waymart',
      holes9: {
        weekday: {
          Morning: { cart: '$14', notes: 'Open-11am' },
          General: { walking: '$12', cart: '$18', notes: '11am-Close' }
        },
        weekend: {
          General: { walking: '$14', cart: '$20', notes: 'All Day' },
        },
      },
      holes18: {
          weekday: {
            Morning: { cart: '$24', notes: 'Open-11am' },
            General: { walking: '$12', cart: '$28', notes: '11am-Close' }
        },
        weekend: {
            General: { walking: '$22', cart: '$20', notes: 'All Day' },
        },
      },
      GeneralNotes: '9 Hole Course | Cash Only | No Tee Time Required',
      website: 'https://www.facebook.com/MemorialLinksGolfCourse/',
      phoneNumber: '(570) 448-9200',
      googlePlaceId: 'ChIJzY1qks8224kRmHXgXdvY_jQ',
      courseLength: '2783 yards'
    },
    {
      id: 'lake-lorain-golf-course',
      name: 'Lake Lorain Golf Course',
      image: '/imgs/lakeLorainLogo.webp',
      rating: '4.4/5',
      ratingLink: 'https://www.google.com/search?sca_esv=41771b6d1dd3ed98&sxsrf=AE3TifPt3pU9Owv6byzBeXZtjhptQF474A:1754246211479&q=lake+lorraine+golf+course&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s5hJRYB1DwIS9qONb6ecgf4ddbup3JxcbY2mAKfswmbKqBVpCp3Wivts9DuX1h-wpMhmFtiuRLHMNpiL9MhXxoGT48BZOXFKv90MVJpIOXMC_1Lc6g%3D%3D&sa=X&ved=2ahUKEwiSr6KypO-OAxWzGVkFHZd0F0wQrrQLegQIKBAA',
      address: '60 Lake Lorain Rd, Poyntelle, PA 18454',
      town: 'Ponytelle',
      holes9: {
        weekday: {
          General: { cart: '$16', notes: 'All Day' }
        },
        weekend: {
          General: { cart: '$19', notes: 'All Day' },
        },
      },
      holes18: {
          weekday: {
          General: { cart: '$23', notes: 'All Day' },
        },
        weekend: {
          General: { cart: '$26', notes: 'All Day' },
        },
      },
      GeneralNotes: '9 Hole Course | Friday Special: 9 Holes $11 / 18 Holes $16',
      website: 'https://www.golflorain.com/',
      phoneNumber: '(570) 448-2232',
      googlePlaceId: 'ChIJAdRA_3A524kRy8pwZCbV8RI',
      courseLength: '2718'
    },
    {
      id: 'red-maples-golf-course',
      name: 'Red Maples Golf Course',
      image: '/imgs/redMapleLogo.png',
      rating: '4.5/5',
      ratingLink: 'https://www.google.com/search?sca_esv=41771b6d1dd3ed98&sxsrf=AE3TifP_A7Z9dAGY46cnnWnuJ_-rkA1v-Q:1754245836074&q=red+maples+golf&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s1m5XMNiFTlsl52flOtxGbiqNy8GlgnYNkLbKvkOjm3OzHnKIJPfwbAvN1SkYm3F-kLXoblkr2jcH7eqHDDYQeSXB5Fp03RdmocFHQIg6t3FOVXbrg%3D%3D&sa=X&ved=2ahUKEwiCuqH_ou-OAxXOE1kFHVt6MUoQrrQLegQIGRAA',
      address: '2322 Easton Turnpike, Waymart, PA 18472',
      town: 'Waymart',
      holes9: {
        weekday: {
          General: { cart: '$22' }
        },
        weekend: {
          General: { cart: '$22' },
        },
      },
      GeneralNotes: '9 Hole Course | Check Facebook page or Call for availability',
      website: 'https://www.facebook.com/redmaplesgolfcourse/',
      phoneNumber: '(570) 937-4543',
      googlePlaceId: 'ChIJT8OBGzzJxIkRQowy4w2JWXU',
      courseLength: '2200 yards'
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