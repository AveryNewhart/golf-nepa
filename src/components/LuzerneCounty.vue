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
      id: 'blue-ridge-trail-golf-club',
      name: 'Blue Ridge Trail Golf Club',
      image: '/imgs/blueRidgeLogo.jpg',
      rating: '4.6/5',
      ratingLink: 'https://www.google.com/search?sca_esv=6f9725795801f4db&sxsrf=AE3TifNrUhXShBmGc_i4n01kCklm478Ftg:1754762472883&q=blue+ridge+trail+golf&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8syr46xfTgO_KMPKZyfPDsLdcSz6GSaeVoZk7fAD_rgHfdH5RNjXcEW_fyGe5-DlCjz5mtXKFBR2PUTGyGwPLxunio293ird5piT3TddIFaaj5M94kg%3D%3D&sa=X&ved=2ahUKEwiL5fHOp_6OAxUwL1kFHZR5Hp8QrrQLegQIKBAA',
      address: '260 Country Club Dr, Mountain Top, PA 18707',
      town: 'Mountain Top',
      holes9: {
        weekday: {
          General: { cart: '$32', notes: 'All Day' }
        },
        weekend: {
          General: { cart: '$34', notes: 'All Day' },
        },
        senior: {
          weekday: { cart: '$32', notes: 'All Day' },
        },
      },
      holes18: {
          weekday: {
          General: { cart: '$46', notes: 'Open-3pm' },
          Twilight: { cart: '$34', notes: 'After 3pm'  }
        },
        weekend: {
          General: { cart: '$56', notes: 'Open-12:30pm' },
          Midday: { cart: '$46', notes: '12:30pm-3pm' },
          Twilight: { cart: '$39', notes: 'After 3pm'  }
        },
        senior: {
          weekday: { cart: '$35', notes: 'All Day' },
        },
      },
      GeneralNotes: '27 Hole Course',
      website: 'https://blueridgetrail.com/',
      phoneNumber: '(570) 868-4653',
      googlePlaceId: 'ChIJL5nJXmsJxYkRuwNMfTM7xjg',
      courseLength: '7095 yards'
    },
    {
      id: 'sand-springs-golf-course',
      name: 'Sand Springs Golf Course',
      image: '/imgs/sandSpringsLogo.avif',
      rating: '4.4/5',
      ratingLink: 'https://www.google.com/search?sca_esv=7b647de37a4058b4&sxsrf=AE3TifPBDBMlhTDqYmNXlcCQEsvAl-JpSA:1754767264373&q=sand+springs+golf+course+drums+pa&si=AMgyJEtREmoPL4P1I5IDCfuA8gybfVI2d5Uj7QMwYCZHKDZ-ExR31yAY5fS-IE2S-owL22nC1_gU4tnzuo6CLL-DW8TOfPlo4ITFFJux0hQeFOzpukF-PdsCzK30J9-Se0Dp5Mr9FIvjEQMUNKbNe4qEPTmu1yfazw%3D%3D&sa=X&ved=2ahUKEwjomdO7uf6OAxWaE1kFHWNxLx8QrrQLegQIGhAA',
      address: '1 Sand Springs Dr, Drums, PA 18222',
      town: 'Drums',
      holes9: {
        weekday: {
          General: { cart: '$30', notes: 'All Day' }
        },
        weekend: {
          General: { cart: '$36', notes: 'All Day' },
        },
        senior: {
          weekday: { cart: '$23', notes: 'All Day' },
          weekend: { cart: '$36', notes: 'All Day' }
        },
      },
      holes18: {
          weekday: {
          General: { walking:'$30', cart: '$43', notes: 'Open-3pm' },
          Twilight: { walking:'$30', cart: '$33', notes: 'After 3pm'  }
        },
        weekend: {
          General: { cart: '$54', notes: 'Open-2pm' },
          Twilight: { walking:'$38', cart: '$38', notes: 'After 2pm'  }
        },
        senior: {
          weekday: { cart: '$34', notes: 'All Day' },
          weekend: { cart: '$50', notes: 'Open-2pm | $36 After 2pm' }
        },
      },
      website: 'https://www.sandspringsgolf.com/',
      phoneNumber: '(570) 788-5845',
      googlePlaceId: 'ChIJFW1Oz98JxYkRuq01k7Oi_J0',
      courseLength: '6612 yards'
    },
    {
      id: 'wilkes-barre-golf-club',
      name: 'Wilkes-Barre Golf Club',
      image: '/imgs/wilkes-barreGcLogo.png',
      rating: '3.9/5',
      ratingLink: 'https://www.google.com/search?sca_esv=9dcc5089927ade44&sxsrf=AE3TifP4OjaMdndih2BjCWe_76q24gWw7A:1754768667313&q=wilkes+barre+municipal+golf+course&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s7lt3ze8x5Nf2xt76u5wAnofIeETEHGlDiYbVV_lqK74D-4xQv0yxhJUgOtJEefFx64MJFDMS0-0fo7KIXK3nOCorCfiQswx6Ebem4xGgO3hDxlEEw%3D%3D&sa=X&ved=2ahUKEwip58_Yvv6OAxU8EFkFHVSpGWkQrrQLegQIJRAA',
      address: '1001 Fairway Dr, Wilkes-Barre, PA 18702',
      town: 'Wilkes-Barre',
      holes18: {
        weekday: {
          General: { cart: '$40', notes: 'Open-3pm' },
          Twilight: { cart: '$28', notes: '3pm-Close' }
        },
        weekend: {
          General: { cart: '$45', notes: 'Open-3pm' },
          Twilight: { cart: '$39', notes: '3pm-Close' }
        },
        senior: {
          weekday: { cart: '$35', notes: 'Open-3pm' },
        },
      },
      GeneralNotes: 'Associated with Hollenback Golf Club',
      website: 'https://www.golfwilkesbarre.com/',
      phoneNumber: '(570) 472-3590',
      googlePlaceId: 'ChIJ84xpQqoExYkRnmuq1tomNYE',
      courseLength: '7010 yards'
    },
    {
      id: 'hollenback-golf-club',
      name: 'Hollenback Golf Club',
      image: '/imgs/hollenbackLogo.jpeg',
      rating: '4/5',
      ratingLink: 'https://www.google.com/search?sca_esv=7b647de37a4058b4&sxsrf=AE3TifPD2X-ADNn3e9TKQ5TrKj1qFoBirQ:1754766754303&q=hollenback+golf+club&si=AMgyJEvkVjFQtirYNBhM3ZJIRTaSJ6PxY6y1_6WZHGInbzDnMRXhHJSHUYYHZEHxgeg875fx3g8aqrZalSWG11ng0lbO_htV1T8jtaoCaSPFWYtHq6_yuTdJ6nvCaQT4OJnmRRgh5GLZRwh1AdcVqshvqnxEEzg5pg%3D%3D&sa=X&ved=2ahUKEwio8bbIt_6OAxX2MVkFHbNkIFMQrrQLegQIHhAA',
      address: '1050 N Washington St, Wilkes-Barre, PA 18705',
      town: 'Wilkes-Barre',
      holes9: {
       weekday: {
          General: { cart: '$23', notes: 'All Day' }
       },
       weekend: {
          General: { cart: '$26', notes: 'All Day' },
       },
      },
      GeneralNotes: '9 Hole Golf Course that is apart of Wilkes-Barre Golf Club',
      website: 'https://www.golfwilkesbarre.com/',
      phoneNumber: '(570) 208-4151',
      googlePlaceId: 'ChIJgZAQTrUbxYkRs5gRCNYicm8',
      courseLength: '2341 yards'
    },
    {
      id: 'edgewood-weddings-and-golf',
      name: 'Edgewood Weddings & Golf',
      image: '/imgs/edgewoodLogo.svg',
      rating: '4.2/5',
      ratingLink: 'https://www.google.com/search?sca_esv=6f9725795801f4db&sxsrf=AE3TifM0zGPhQi-9lHiWG1BMR0OCYOHkyg:1754763066457&q=edgewood+in+the+pines&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s3cgbvMBC7McgLi9Dvj_9C62liHws_oiA5trfjH74S3yk-n4owzBOTN7CWB2VAEXRCOdu9TAtKJVl-vEnr_0JCjcS6ZZmfsWOALgv1HRln2UpHno2Q%3D%3D&sa=X&ved=2ahUKEwjP0Pbpqf6OAxV3MlkFHWOoDZ8QrrQLegQIHBAA',
      address: '22 Edgewood Rd, Drums, PA 18222',
      town: 'Drums',
      holes9: {
        weekday: {
          General: { cart: '$23', notes: 'All Day' }
        },
        weekend: {
          General: { cart: '$26', notes: 'All Day' },
        },
      },
      holes18: {
          weekday: {
          General: { cart: '$34', notes: 'All Day' },
        },
        weekend: {
            General: { cart: '$38', notes: 'All Day' },
        },
      },
      GeneralNotes: '9 Hole Course | Golf Simulators | Disc Golf',
      website: 'https://www.edgewoodpa.com/',
      phoneNumber: '(570) 788-1101',
      googlePlaceId: 'ChIJKy_lsz2nxYkRcVSvtG4gluo',
      courseLength: '6482 yards'
    },
    {
      id: 'four-seasons-golf-club',
      name: 'Four Seasons Golf Club',
      image: '/imgs/fourSeasonExeterLogo.jpeg',
      rating: '3.6/5',
      ratingLink: 'https://www.google.com/search?sca_esv=6f9725795801f4db&sxsrf=AE3TifMCJrRqqOc3lowzBO7hMqY7yM3Lrg:1754763848802&q=four+seasons+golf+club+exeter+pa&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s37zaLUioqrR0ZUfBPqwhaQgOILxJRKJqS6k5HjcCYVQ3IMreTYcHFTHoIoZwvIqm25NdGDGZzCgQoAMbBm_HUefJBxe_la--7i6DNj5ADGUhFr78Q%3D%3D&sa=X&ved=2ahUKEwjdoP3erP6OAxWoFlkFHU09B_YQrrQLegQIHhAA',
      address: '332 Slocum Ave, Exeter, PA 18643',
      town: 'Exeter',
      holes18: {
        weekday: {
          General: { cart: '$31.50', notes: 'Open-3pm' },
          Twilight: { cart: '$24', notes: '3pm-Close' }
        },
        weekend: {
          General: { cart: '$36', notes: 'Open-3pm' },
          Twilight: { cart: '$38', notes: '3pm-Close' }
        },
      },
      website: 'https://www.facebook.com/fourseasonsgolfclub/',
      phoneNumber: '(570) 655-8869',
      googlePlaceId: 'ChIJ_4BUXt0YxYkRuPbRP5YLbyQ',
      courseLength: '5524 yards'
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
  