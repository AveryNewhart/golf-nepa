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
      id: 'towanda-country-club',
      name: 'Towanda Country Club',
      image: '/imgs/towandaCcLogo.png',
      rating: '4.1/5',
      ratingLink: 'https://www.google.com/search?q=towanda+country+club+reviews&sca_esv=41771b6d1dd3ed98&sxsrf=AE3TifOJYkVLp1cRQwY2mIRO-WS-hPQCfg%3A1754244077791&ei=7aOPaMP6L97l5NoPrPTvaA&ved=0ahUKEwiDpey4nO-OAxXeMlkFHSz6Gw0Q4dUDCBA&uact=5&oq=towanda+country+club+reviews&gs_lp=Egxnd3Mtd2l6LXNlcnAaAhgCIhx0b3dhbmRhIGNvdW50cnkgY2x1YiByZXZpZXdzMgUQIRigATIFECEYoAFIlA5Q2gVY1g1wAXgAkAEAmAF-oAGtBaoBAzcuMbgBA8gBAPgBAZgCCKACzgTCAgoQABiwAxjWBBhHwgINEAAYsAMY1gQYRxiLA8ICBRAAGIAEwgIGEAAYFhgewgIFEAAY7wXCAggQABiABBiiBMICBRAhGKsCmAMAiAYBkAYIkgcBOKAHjyCyBwE3uAfIBMIHBTIuMy4zyAcT&sclient=gws-wiz-serp#',
      address: '645 Golden Mile Rd, Towanda, PA 18848',
      town: 'Towanda',
      holes9: {
        weekday: {
          General: { walking: '$20', cart: '$35', notes: 'All Day' }
        },
        weekend: {
          General: { walking: '$20', cart: '$35', notes: 'All Day' },
        },
        senior: {
          weekday: { walking: '$15', cart: '$30', notes: 'Same as Weekend' },
        },
      },
      holes18: {
        weekday: {
          General: { walking: '$27', cart: '$52', notes: 'All Day' }
        },
        weekend: {
          General: { walking: '$27', cart: '$52', notes: 'All Day' },
        },
        senior: {
          weekday: { walking: '$17', cart: '$42', notes: 'Same as Weekend' },
        },
      },
      GeneralNotes: 'Senior is 65+',
      website: 'https://www.towandagolfclub.com/',
      phoneNumber: '(570) 265-6222',
      googlePlaceId: 'ChIJ1fD4CJeq2okRR6CbsbfLogE',
      courseLength: '6060 yards'
    },
    {
        //NEED TO GET PINECROFT RATE INFO STILL !!!!!!!!! 


      id: 'pinecroft-golf-course',
      name: 'Pinecroft Golf Course',
      image: '/imgs/pinecroftLogo.png',
      rating: '4.4/5',
      ratingLink: 'https://www.google.com/search?sca_esv=41771b6d1dd3ed98&sxsrf=AE3TifO9LXNDUI87rLaey7FKnjnrwemBSw:1754244486694&q=pinecroft+golf+course+pa&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s5qkUtALc0_lODGYbipxiYIp7riyXg06dZC6p-do2rhk-XOWz5PgMLtEzYWoh7Qt5b8pCd4jV9Rau1e7aIMvYAOFtSFaaJamCYpXwFaN_ZBs1yIaoA%3D%3D&sa=X&ved=2ahUKEwja9On7ne-OAxWDEFkFHdLGJB0QrrQLegQIHRAA',
      address: '2551 Centerville Rd, Gillett, PA 16925',
      town: 'Gillett',
      holes9: {
        weekday: {
          General: { walking: '$20', cart: '$28', notes: 'All Day' }
        },
        weekend: {
          General: { walking: '$26', cart: '$34', notes: 'All Day' },
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
      },
      GeneralNotes: '9 Hole Course',
      website: 'https://www.facebook.com/people/Pinecroft-Golf-Course/100063524350593/#',
      phoneNumber: '(570) 596-4653',
      googlePlaceId: 'ChIJIzcdADwwxYkRbUk1_n3H0JY',
      courseLength: '2778 yards'
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
  