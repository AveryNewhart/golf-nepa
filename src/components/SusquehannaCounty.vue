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
      id: 'rock-creek-golf-course',
      name: 'Rock Creek Golf Course',
      image: '/imgs/rockCreekLogo.jpeg',
      rating: '4.3/5',
      ratingLink: 'https://www.google.com/search?sca_esv=ded0a181c7cc7b88&sxsrf=AE3TifMAOrDjbztfZXPYTDC_1FPPU7KtUw:1754235110241&q=rock+creek+golf+course+pa&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s5FPTKNDE6gpM5tNjqWUiLUt7RrpeBqueHPvZkkHHzB5yFflO2QVvHE0a_snSSQgXpcsAQkEPUgUdD-_KmQsSD3nZy30x2aNxLb32oA-Kg6XJo18-g%3D%3D&sa=X&ved=2ahUKEwijvOSE--6OAxWvMmIAHXWuIucQrrQLegQIMBAA',
      address: '2783 PA-374, Nicholson, PA 18446',
      town: 'Nicholson',
      holes9: {
        weekday: {
          General: { walking: '$12', cart: '$20', notes: 'All Day' }
        },
        weekend: {
          General: { walking: '$14', cart: '$22', notes: 'All Day' },
        },
        senior: {
          weekday: { cart: '$18', notes: 'All Day' },
          weekend: { cart: '$20', notes: 'All Day' }
        },
      },
      holes18: {
          weekday: {
          General: { walking: '$22', cart: '$30', notes: 'All Day' },
        },
        weekend: {
          General: { walking: '$24', cart: '$32', notes: 'All Day' },
        },
        senior: {
          weekday: { cart: '$27', notes: 'All Day' },
          weekend: { cart: '$30', notes: 'All Day' }
        },
      },
      GeneralNotes: 'Senior is 65+',
      website: 'https://www.facebook.com/rcgolf/',
      phoneNumber: '(570) 222-2500',
      googlePlaceId: 'ChIJEZ_WBUzVxIkRpdVfQi_2ofo',
      courseLength: '4616 yards'
    },
    {
      id: 'tall-pines-players-club',
      name: 'Tall Pines Players Club',
      image: '/imgs/tallPinesLogo.png',
      rating: '4.7/5',
      ratingLink: 'https://www.google.com/search?sca_esv=ded0a181c7cc7b88&sxsrf=AE3TifPoQ915QqTt6zXwLKW7dEveb9IJww:1754236152106&q=tall+pines+golf+course+pa&si=AMgyJEvkVjFQtirYNBhM3ZJIRTaSJ6PxY6y1_6WZHGInbzDnMXtp8mMVdVZ_sT55EqCVaLq-rSr92ccwHeKR_XsPnHbrP-h8BXKTIiYulaAyavr5V_SR5zejlBRFGDYN0-fqIZ0sV_tOm_HhSrSlAWfjm6hjNW4w7Q%3D%3D&sa=X&ved=2ahUKEwi3-8r1_u6OAxW2E1kFHUSNOCwQrrQLegQIGhAA',
      address: '628 Kinney Rd, Friendsville, PA 18818',
      town: 'Friendsville',
      holes9: {
        weekday: {
          General: { walking: '$25', cart: '$37', notes: 'All Day' }
        },
        weekend: {
          General: { walking: '$28', cart: '$40', notes: 'All Day' },
        },
      },
      holes18: {
          weekday: {
          General: { walking: '$32', cart: '$50', notes: 'Open-3pm' },
          Twilight: { cart: '$39', notes: 'After 3pm'  }
        },
        weekend: {
          General: { walking: '$37', cart: '$55', notes: 'Open-3pm' },
          Twilight: { cart: '$39', notes: 'After 3pm'  }
        },
        senior: {
          weekday: { cart: '$39', notes: 'All Day' },
        },
      },
      GeneralNotes: 'Military Rates Same as Senior',
      website: 'https://tallpinesplayersclubllc.com/',
      phoneNumber: '(570) 553-4653',
      googlePlaceId: 'ChIJ2-hKuZPG2okR4OvrB3tZlcs',
      courseLength: '5408 yards'
    },
    {
      id: 'panorama-golf-course',
      name: 'Panorama Golf Course',
      image: '/imgs/panoramaGolfLogo.jpeg',
      rating: '4.3/5',
      ratingLink: 'https://www.google.com/search?sca_esv=ded0a181c7cc7b88&sxsrf=AE3TifO-PaZoWc6zvrxutuhfYE77rhdJNA:1754236490637&q=panorama+golf+course+pa&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s4110SfyxjEmAu52lu624yBb3tdGAOzorf5bVwRic51vc6oC6Xvp3vIwBXjCkyZAlKBmaLQutKrVYfu0wcBL3jrx78JNN8M-vCBjj0i8g0OrXQGcfg%3D%3D&sa=X&ved=2ahUKEwjmloGXgO-OAxXqFFkFHVgcNuIQrrQLegQIIxAA',
      address: '1124 State Rte 2023, Clifford Township, PA 18421',
      town: 'Clifford Township',
      holes9: {
        weekday: {
          General: { walking: '$13', cart: '$21', notes: 'All Day' }
        },
        weekend: {
          General: { walking: '$16', cart: '$24', notes: 'All Day' },
        },
        senior: {
          weekday: { walking: '$11', cart: '$19', notes: 'All Day' },
          weekend: { walking: '$14', cart: '$22', notes: 'All day' }
        },
      },
      holes18: {
          weekday: {
          General: { walking: '$21', cart: '$37', notes: 'All Day' },
        },
        weekend: {
          Morning: { walking: '$26', cart: '$42', notes: 'ONLY UNTIL 12PM' },
        },
        senior: {
          weekday: { walking: '$16', cart: '$32', notes: 'All Day' },
          weekend: { walking: '$23', cart: '$39', notes: 'ONLY UNTIL 12PM' }
        },
      },
      GeneralNotes: 'Senior is 16+',
      website: 'https://www.panoramagolfcourse.com/',
      phoneNumber: '(570) 222-3525',
      googlePlaceId: 'ChIJT3U6dCcz24kReywd0KeJhxM',
      courseLength: '7095 yards'
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
  