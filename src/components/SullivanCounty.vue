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
const courses: Course[] = [];
</script>

<template>
  <div v-if="courses.length === 0" class="no-courses-message">
    There are currently no public courses in Sullivan County
  </div>
  <CourseCardTemplate
    v-else
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
.no-courses-message {
  text-align: center;
  padding: 2rem;
  font-size: 1.2rem;
  color: #666;
}
</style>