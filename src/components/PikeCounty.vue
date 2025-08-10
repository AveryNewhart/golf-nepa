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
      id: 'cliff-park-golf-course',
      name: 'Cliff Park Golf Course',
      image: '/imgs/cliffParkLogo.jpeg',
      rating: '4.5/5',
      ratingLink: 'https://www.google.com/search?sca_esv=1b131cb33424c794&sxsrf=AE3TifPK4zOmLKGjVFcYen8DaNm8Lnj9ig:1754525244319&q=cliff+park+golf+course&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8sygXpM3DJowX2NNQZAiLkSvjO1avTOAcmlC1C92l9N3-0qZ5SKoc_u9vEGxcC6pE_fyjA7q9aifRozNgoLERzMQQl4potsticiCt2q3yNHSgFZ7qMA%3D%3D&sa=X&sqi=2&ved=2ahUKEwjSo7_vs_eOAxUPF1kFHQ6lDxkQrrQLegQIHRAA',
      address: '155 Cliff Park Rd, Milford, PA 18337',
      town: 'Milford',
      holes9: {
        weekday: {
          General: { cart: '$20', notes: 'All Day' },
        },
        weekend: {
          General: { notes: 'Same as weekday' },
        },
      },
      holes18: {
          weekday: {
          General: { cart: '$30', notes: 'All Day' },
        },
        weekend: {
          General: { notes: 'Same as weekday' },
        },
      },
      GeneralNotes: '9 Hole Course',
      website: 'https://www.facebook.com/profile.php?id=100063709866582',
      phoneNumber: '(570) 995-1274',
      googlePlaceId: 'ChIJCeVsJYdbw4kRm9G5-UAHtBI',
      courseLength: '3115 yards'
    },
    {
      id: 'paupack-hills-golf-course',
      name: 'Paupack Hills Golf Course',
      image: '/imgs/paupackHillsLogo.png',
      rating: '4.9/5',
      ratingLink: 'https://www.google.com/search?sca_esv=1b131cb33424c794&sxsrf=AE3TifN2hu-GI2b0EB5SdvXSZAKl6g8U8w:1754526555529&q=paupack+hills+golf+course&si=AMgyJEtREmoPL4P1I5IDCfuA8gybfVI2d5Uj7QMwYCZHKDZ-E2CKab0Z-r6HCe4vWik6yxk4oJ1xp1zUWHaU5uC4dZf64q6qFgMjjZM0PT5-Z9EOV9YBU41UBHlbhltwMnTV2KTKtPHGuCfofdLrmyRc_4vJ6ZzWhA%3D%3D&sa=X&ved=2ahUKEwjtmN3guPeOAxUKD1kFHR3_Bx4QrrQLegQIGhAA',
      address: '125 Country Club Rd, Greentown, PA 18426',
      town: 'Greentown',
      holes9: {
        weekday: {
          General: { cart: '$45', notes: 'Open-2pm' },
          Twilight: { cart: '$35', notes: '2pm-Close' }
        },
        weekend: {
          General: { cart: '$55', notes: 'Open-2pm' },
          Twilight: { cart: '$45', notes: '2pm-Close' }
        },
      },
      holes18: {
        weekday: {
          General: { cart: '$55', notes: 'Open-2pm' },
          Twilight: { cart: '$45', notes: '2pm-Close' }
        },
        weekend: {
          General: { cart: '$65', notes: 'Open-2pm' },
          Twilight: { cart: '$55', notes: '2pm-Close' }
        },

      },
      GeneralNotes: 'For tee times call clubhouse | 10% Discount for seniors, vets, and first responders',
      website: 'https://www.facebook.com/paupack.hills',
      phoneNumber: '(570) 776-8016',
      googlePlaceId: 'ChIJY3cdB0K7xIkRk9tlacImTxo',
      courseLength: '6452 yards'
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
  