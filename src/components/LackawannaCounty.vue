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
      id: 'homestead-golf-course',
      name: 'Homestead Golf Course',
      image: '/imgs/homesteadLogo.webp',
      rating: '4.5/5',
      ratingLink: 'https://www.google.com/search?sca_esv=7d0b40d4ccf1baac&sxsrf=AE3TifOckqzHdVO926a3FzMki3oTatuqxQ:1754438296451&q=homestead+golf+course+fell+twp+pa&si=AMgyJEtREmoPL4P1I5IDCfuA8gybfVI2d5Uj7QMwYCZHKDZ-E_-OGAdu8L-8qAcUdATYPgZjjXzfqa4kx0u9IE5WxyFN1hG0lCUIz290wPK9k9ewZH2BPOGX8zacKdOvya5e1sIt_wsYpVaXcxeTSSC8jMTb7GiDbg%3D%3D&sa=X&ved=2ahUKEwiNx8L77_SOAxW9F1kFHUKxEp4QrrQLegQIGxAA',
      address: 'Fallbrook St, Carbondale, PA 18407',
      town: 'Carbondale',
      holes9: {
        weekday: {
          General: { walking: '$12', cart: '$20', notes: 'All Day' }
        },
        weekend: {
          General: { notes: 'SAME AS WEEKDAY' },
        },
        senior: {
          weekday: { walking: '$10', cart: '$15', notes: 'BEFORE 1PM ONLY' },
        },
      },
      holes18: {
        weekday: {
          General: { walking: '$20', cart: '$35', notes: 'All Day' }
        },
        weekend: {
          General: { notes: 'SAME AS WEEKDAY' },
        },
        senior: {
          weekday: { walking: '$18', cart: '$30', notes: 'BEFORE 1PM ONLY' },
        },
      },
      website: 'https://www.homesteadgolfpa.com/',
      phoneNumber: '(484) 574-3685',
      googlePlaceId: 'ChIJaw5sJYbTxIkRsvxwfeVqpYg',
      courseLength: '4821 yards'
    },
    {
      id: 'pine-hills-country-club',
      name: 'Pine Hills Country Club',
      image: '/imgs/pineHillsCcLogo.png',
      rating: '4.4/5',
      ratingLink: 'https://www.google.com/search?sca_esv=7d0b40d4ccf1baac&sxsrf=AE3TifNFNs2UhoswbxDrKRrxwNm-6adSbw:1754440836852&q=pine+hills+country+club+pa&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s7KHlCKfb2AyxOBGhLZNpe7vAnxMjq1qhAhX6ULtVlhdnTDdS23dOyBfmv1n3MS6HnF_l_QJkK8FJNb9Nv7q5LK4UHlj4I8rAAlY15a3kvouUILWfQ%3D%3D&sa=X&ved=2ahUKEwiXt_C2-fSOAxV7EGIAHdjGNTwQrrQLegQIGhAA',
      address: '140 S Keyser Ave, Taylor, PA 18517',
      town: 'Taylor',
      holes9: {
        weekday: {
          General: { walking: '$16', cart: '$23', notes: 'All Day' }
        },
        weekend: {
          General: { walking: '$18', cart: '$25', notes: 'After 11am' },
        },
        senior: {
          weekday: { walking: '$13', cart: '$20', notes: 'After 10am' },
        },
      },
      holes18: {
          weekday: {
          General: { walking: '$21', cart: '$35', notes: 'All Day' },
        },
        weekend: {
          General: { walking: '$27', cart: '$41', notes: 'Open-1pm' },
          Twilight: { walking: '$23', cart: '$31', notes: 'After 1pm'  }
        },
        senior: {
          weekday: { walking: '$17', cart: '$31', notes: 'All Day' },
        },
      },
      GeneralNotes: 'Par 3 Course & Footgolf $8 | Golf Simulators',
      website: 'https://www.pinehillscc.net/',
      phoneNumber: '(570) 562-0138',
      googlePlaceId: 'ChIJ1ee92J4gxYkR0Fpyojl8VG4',
      courseLength: '6100 yards'
    },
    {
      id: 'sleepy-hollow-golf-course',
      name: 'Sleepy Hollow Golf Course',
      image: '/imgs/sleepyHollowLogo.png',
      rating: '4.2/5',
      ratingLink: 'https://www.google.com/search?sca_esv=7d0b40d4ccf1baac&sxsrf=AE3TifOBPhFHeWSezaC--fkUDck8lmwH0g:1754442301216&q=sleepy+hollow+golf+course+pa&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s3DKrtb8Z-DPWz2jNxxk-smIBinb7mvruSANbPfcDWf_sQKecqJKDl7trleZF371DLWDe_keHVGWAyj2ja8XDHAvi5sDeMbBGprof5Ftj5SvrRlEuQ%3D%3D&sa=X&ved=2ahUKEwj7jZLx_vSOAxX6EVkFHU6QEyIQrrQLegQIHRAA',
      address: '140 Sandy Banks Rd, Greenfield Township, PA 18407',
      town: 'Greenfield Twp',
      holes9: {
        weekday: {
          General: { walking: '$14', cart: '$22', notes: 'All Day' }
        },
        weekend: {
          General: { walking: '$16', cart: '$24', notes: 'All Day' },
        },
        senior: {
          weekday: { walking: '$11', cart: '$17', notes: 'All Day' },
          weekend: { notes: 'Same as Weekday' }
        },
      },
      holes18: {
        weekday: {
          General: { walking: '$26', cart: '$40', notes: 'All Day' }
        },
        weekend: {
          General: { walking: '$32', cart: '$45', notes: 'All Day' },
        },
        senior: {
          weekday: { walking: '$21', cart: '$32', notes: 'All Day' },
          weekend: { notes: 'Same as Weekday' }
        },
      },
      GeneralNotes: '19 Hole Course | $2 more for just back 10',
      website: 'https://sleepyhollowgolfcourse.com/nsite/',
      phoneNumber: '(570) 254-4653',
      googlePlaceId: 'ChIJ1_8SzkfSxIkRfEwtE3EMcHQ',
      courseLength: '5546 yards'
    },
    {
      id: 'wemberly-hills-golf-course',
      name: 'Wemberly Hills Golf Course',
      image: '/imgs/wemberlyHillsLogo.png',
      rating: '4.4/5',
      ratingLink: 'https://www.google.com/search?sca_esv=38b8b35f2fe0540c&sxsrf=AE3TifPVBiwAXVaLlZBZLbLTcO_60HW6Gg:1754447191346&q=wemberly+hills+golf+course&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s-5c7G95RHdkcJ5HMNp9cb2T47_7bq7umYGJrRv4C9unz9r9wMo51CbJFDHriN5TBBU7cNkjeS-i5j1oRwNs9IMylsgUOWTAG-ZWm528RkMUqmN_kA%3D%3D&sa=X&ved=2ahUKEwjA-_eMkfWOAxXnD1kFHZ35IWAQrrQLegQIGhAA',
      address: '66 Club House Ln, Olyphant, PA 18447',
      town: 'Olyphant',
      holes9: {
        weekday: {
          General: { walking: '$15', cart: '$19.72', notes: 'All Day' }
        },
        weekend: {
          General: { walking: '$15', cart: '$22.66', notes: 'All Day' },
        },
        senior: {
          weekday: { walking: '$12', cart: '$18.72', notes: 'All Day' },
          weekend: { walking: '$14', cart: '$21.66', notes: 'All Day' },
        },
      },
      GeneralNotes: '9 Hole Course | CALL CLUBHOUSE TO PLAY 18 | Golf Simulators | Veteran discount, same rate as Senior',
      website: 'https://wemberlyhillsgc.com/',
      phoneNumber: '(570) 563-1902',
      googlePlaceId: 'ChIJfdNwN8fWxIkRjmjlL5dKlSM',
      courseLength: '2944 yards'
    },
        {
      id: 'scott-greens-golf-club',
      name: 'Scott Greens Golf Club',
      image: '/imgs/scottGreenLogo.jpg',
      rating: '4.4/5',
      ratingLink: 'https://www.google.com/search?sca_esv=7d0b40d4ccf1baac&sxsrf=AE3TifNlY2enQGlveU8xxOUiLYCOwKGNMw:1754441788330&q=scott+greens+golf&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s_87o8MtAeUSKGheCjjV4dhksnhogozbqbxqkUFlU-H-i-d65_ljYVAXg8UCbCHUd5g1k5zMKNYPoed3GwtvKTuLW6bKFvdfSJdDT4j9PY24GytygA%3D%3D&sa=X&ved=2ahUKEwiMhcr8_PSOAxVaD1kFHTcwIk8QrrQLegQIHhAA',
      address: '455 Green Grove Rd, Scott, PA 18447',
      town: 'Scott',
      holes9: {
        weekday: {
          General: { cart: '$15', notes: 'All Day + Weekend Rates' }
        },
      },
      GeneralNotes: '9 Hole Course | golf Simulators',
      website: 'https://www.scottgreensgolfclub.com/',
      phoneNumber: '(570) 254-6979',
      googlePlaceId: 'ChIJUVq6tsvQxIkRJrlU5YCP13A',
      courseLength: '1983 yards'
    },
    {
      id: 'marjon-golf-course',
      name: 'Marjon Golf Course',
      image: '/imgs/marjonGolfLogo.png',
      rating: '4.4/5',
      ratingLink: 'https://www.google.com/search?sca_esv=7d0b40d4ccf1baac&sxsrf=AE3TifPGECsprGp3_PvNU7YT1JY3ki8_lg:1754439048381&q=marjon+golf+course&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s66HmVztU-bLS7T28Le65YOxdLrdiT1iOOB-IWeVd79hILrnQyp3lSnpacawn_N89-A7VW3gwUn0m8O9Ilj7GLzvnwu78S4KE1exS0Vntfyb7FhXBg%3D%3D&sa=X&ved=2ahUKEwix5Iji8vSOAxVPEVkFHd_CB0AQrrQLegQIHBAA',
      address: '1360 Griffin Rd, Roaring Brook Township, PA 18444',
      town: 'Roaring Brook Twp',
      GeneralNotes: '9 Hole Course',
      website: 'https://www.facebook.com/profile.php?id=100066500558894#',
      phoneNumber: '(570) 842-7922',
      googlePlaceId: 'ChIJL8KOWE7DxIkRYgZaat0wDQM',
      courseLength: '2691 yards'
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
  