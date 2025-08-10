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
      id: 'the-poconos-club',
      name: 'The Poconos Club',
      image: '/imgs/thePoconosClubLogo.png',
      rating: '4.2/5',
      ratingLink: 'https://www.google.com/search?sca_esv=e03d869ac8eda435&sxsrf=AE3TifPbMzZMoHtVvnAH0Fk9QI96k-71pg:1754788852694&q=country+club+of+the+poconos+municipal+golf+course&si=AMgyJEvkVjFQtirYNBhM3ZJIRTaSJ6PxY6y1_6WZHGInbzDnMbjbkkh6NxOM3mN9qw7gFcBc2KXi9tiu_bNj35x0lP-PXLGCEH7gmLLYCWZn0aC5hlTyiPfd4Z6Ej8o_t9F2pmmrRj-A&sa=X&ved=2ahUKEwiZ2-Hxif-OAxU1F1kFHSlZGKgQrrQLegQIHxAA',
      address: '1445 Big Ridge Dr, East Stroudsburg, PA 18302',
      town: 'East Stroudsburg',
      holes9: {
        weekday: {
          General: { cart: '$35', notes: 'All Day' }
        },
        weekend: {
          General: { cart: '$40', notes: 'All Day' },
        },
      },
      holes18: {
        weekday: {
          General: { cart: '$50', notes: 'Open-2pm' },
          Twilight: { cart: '$45', notes: '2pm-Close' }
        },
        weekend: {
          Morning: { cart: '$60', notes: 'Open-11am' },
          Midday: { cart: '$50', notes: '11am-2pm' },
          Twilight: { cart: '$40', notes: '2pm-Close' }
        },
        senior: {
          weekday: { cart: '$35', notes: 'Mon-Thur' },
        },
      },
      GeneralNotes: 'Tuesday Special $35 Everyone',
      website: 'https://thepococlub.com/',
      phoneNumber: '(570) 223-8099',
      googlePlaceId: 'ChIJ4eYUou-ExIkRQ25HCUVZof0',
      courseLength: '5900 yards'
    },
    {
      id: 'skytop-lodge',
      name: 'Skytop Lodge',
      image: '/imgs/skytopLodgeLogo.avif',
      rating: '4.6/5',
      ratingLink: 'https://www.google.com/travel/search?g2lb=4965990,4969803,72302247,72317059,72414906,72471280,72472051,72485658,72560029,72573224,72616120,72647020,72648289,72686036,72760082,72803964,72832976,72882230,72958624,72959983,72990341&hl=en-US&gl=us&cs=1&ssta=1&q=skytop+lodge+golf+course&ts=CAEaRwopEicyJTB4ODljNDk3OGQ3MzViMzNiNzoweGRkZTI5NGM5OTY0MDlkYzQSGhIUCgcI6Q8QCRgJEgcI6Q8QCRgKGAEyAhAA&qs=CAEyFENnc0l4THVDc3BtWnBmSGRBUkFCOAJCCQnEnUCWyZTi3UIJCcSdQJbJlOLd&ap=ugEHcmV2aWV3cw&ictx=111&ved=1t:1250',
      address: '1 Skytop Dr, Skytop, PA 18357',
      town: 'Skytop',
      holes9: {
        weekday: {
          General: { cart: '$40', notes: 'Open-2pm' },
          Twilight: { cart: '$45', notes: '2pm-Close' }
        },
        weekend: {
          General: { cart: '$60', notes: 'Open-2pm' },
          Twilight: { cart: '$55', notes: '2pm-Close' }
        },
      },
      holes18: {
        weekday: {
          General: { cart: '$80', notes: 'Open-2pm' },
          Twilight: { cart: '$65', notes: '2pm-Close' }
        },
        weekend: {
          General: { cart: '$100', notes: 'Open-2pm' },
          Twilight: { cart: '$90', notes: '2pm-Close' }
        },
      },
      website: 'https://www.skytop.com/?utm_source=local&utm_medium=organic&utm_campaign=gbp&utm_content=Lodge',
      phoneNumber: '(570) 257-2114',
      googlePlaceId: 'ChIJtzNbc42XxIkRxJ1AlsmU4t0',
      courseLength: '6656 yards'
    },
    {
      id: 'shawnee-inn-and-golf-resort',
      name: 'Shawnee Inn & Golf Resort',
      image: '/imgs/shawneeInnLogo.svg',
      rating: '4/5',
      ratingLink: 'https://www.google.com/travel/search?g2lb=4965990,4969803,72302247,72317059,72414906,72471280,72472051,72485658,72560029,72573224,72616120,72647020,72648289,72686036,72760082,72803964,72832976,72882230,72958624,72959983,72990341&hl=en-US&gl=us&cs=1&ssta=1&q=shawnee+inn+and+golf+resort&ts=CAEaRwopEicyJTB4ODljNDg2NjAwZjRhMjkyNzoweDRkY2U3OTcyZTExNTk1OTYSGhIUCgcI6Q8QCxgREgcI6Q8QCxgSGAEyAhAA&qs=CAEyE0Nnb0lscXZXaUs2dW51ZE5FQUU4AkIJCZaVFeFyec5NQgkJlpUV4XJ5zk0&ap=ugEHcmV2aWV3cw&ictx=111&ved=1t:1250&cshid=1754794274623340',
      address: '100 Shawnee Inn Dr, Shawnee on Delaware, PA 18356',
      town: 'Shawnee on Deleware',
      holes18: {
        weekday: {
          Twilight: { cart: '$40', notes: 'After 4pm Only' }
        },
        weekend: {
          Twilight: { notes: 'Same as Weekday' },
        },
      },
      GeneralNotes: 'AFTER 4PM ONLY | Semi-private | 27 Hole Course(3 9 Hole Courses)',
      website: 'https://www.shawneeinn.com/?utm_source=google&utm_medium=organic&utm_campaign=business_listing',
      phoneNumber: '(570) 424-4000',
      googlePlaceId: 'ChIJJylKD2CGxIkRlpUV4XJ5zk0',
      courseLength: '3227-34238 yards'
    },
    {
      id: 'pocono-manor-golf-course',
      name: 'Pocono Manor Golf Course',
      image: '/imgs/poconoManorCcLogo.webp',
      rating: '3.8/5',
      ratingLink: 'https://www.google.com/search?sca_esv=84546c4646d709ac&sxsrf=AE3TifNHARN-8ztMQWf80bScTP0BJ3LA6w:1754793641349&q=pocono+manor+golf&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s9fWg4Ln1Panq8gv00Tv7CpDb4ETee2ZgRXpw6YZy6Wi3vDue6B20d60qJBt__9YAd7Yhj3xUruzEhODSkICIKM7pohmki-m-JpI7C8T937HtKw_uw%3D%3D&sa=X&ved=2ahUKEwjS-ZXdm_-OAxV9EFkFHeQ4CrIQrrQLegQIIxAA',
      address: '395 Manor Dr, Pocono Manor, PA 18349',
      town: 'Pocono Manor',
      holes18: {
        weekday: {
          General: { cart: '$47', notes: 'Open-3pm' },
          Twilight: { cart: '$37', notes: '3pm-Close' }
        },
        weekend: {
          Morning: { cart: '$77', notes: 'Open-Noon' },
          Midday: { cart: '$72', notes: 'Noon-3pm' },
          Twilight: { cart: '$55', notes: '3pm-Close' },
        },
        senior: {
          weekday: { cart: '$35', notes: 'Mon-Thur' },
        },
      },
      GeneralNotes: 'Senior is 60+',
      website: 'https://www.golfpoconomanor.com/',
      phoneNumber: '(570) 839-1389',
      googlePlaceId: 'ChIJnVsWb5WJxIkRXSpSQCASOZU',
      courseLength: '6063 yards'
    },
    {
      id: 'mount-airy-golf-club',
      name: 'Mount Airy Golf Club',
      image: '/imgs/mountAiryLogo.png',
      rating: '4.5/5',
      ratingLink: 'https://www.google.com/search?sca_esv=84546c4646d709ac&sxsrf=AE3TifNSxwWbCg-ZAWjgXm_P6BLXL1xUkg:1754792570808&q=mount+airy+golf+course&si=AMgyJEvkVjFQtirYNBhM3ZJIRTaSJ6PxY6y1_6WZHGInbzDnMZmbBa098F1xHITF2P51s9s0PB_Zy_QtDozm4UaGn8shcBytQ-0GVFg52LwI6gFU6Pm_gg_1cutyu-kFSQW21GAMSZTFlcJ2BsPEWiGZQlCkiBTTVA%3D%3D&sa=X&ved=2ahUKEwidq9nel_-OAxU0D1kFHcw3EMkQrrQLegQIIBAA',
      address: '312 Woodland Rd, Mt Pocono, PA 18344',
      town: 'Mt Pocono',
      holes9: {
        weekday: {
          General: { cart: '$45', notes: 'All Day' }
        },
        weekend: {
          General: { cart: '$55', notes: 'After 2pm Only' },
        },
      },
      holes18: {
        weekday: {
          General: { cart: '$67', notes: 'Open-3pm' },
          Twilight: { cart: '$45', notes: '3pm-Close' }
        },
        weekend: {
          General: { cart: '$97', notes: 'Open-3pm' },
          Twilight: { cart: '$75', notes: '3pm-Close' }
        },
        senior: {
          weekday: { cart: '$47', notes: 'Open-3pm' },
        },
      },
      website: 'https://mountairycasino.com/golf/?utm_source=gbp&utm_medium=organic&utm_campaign=Mount_Airy_Golf',
      phoneNumber: '(570) 243-5240',
      googlePlaceId: 'ChIJUSVKV0CNxIkRRModM6BDJww',
      courseLength: '6500 yards'
    },
    {
      id: 'indian-mountain-golf-course',
      name: 'Indian Mountain Golf Course',
      image: '/imgs/indianMountainLogo.avif',
      rating: '4.1/5',
      ratingLink: 'https://www.google.com/search?sca_esv=b0cd922a17076a66&sxsrf=AE3TifMG9MDJYFkeiSXZ94-YnmoVWLhM2g:1754796050226&q=indian+mountain+golf+course&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s01h-rdJKdzlYhlZoRrcsUJ6OuhLIAocaGomim0b1UX2HZ1e5cmGtjobZBH7719Y9HY_m31GjRLSYnCJt2ffo0twi6YSOZFgLEahZn1uLTZF-X0vww%3D%3D&sa=X&ved=2ahUKEwjJl-jZpP-OAxXxKVkFHV43GI0QrrQLegQIJhAA',
      address: '162 Indian Mountain Drive, Kresgeville, PA 18333',
      town: 'Krsgeville',
      holes9: {
        weekday: {
          General: { walking: '$14', cart: '$23', notes: 'All Day' },
        },
        weekend: {
          General: { walking: '$20', cart: '$28', notes: 'All Day' },
        },
        senior: {
          weekday: { cart: '20', notes: 'Mon-Thur' },
        },
      },
      holes18: {
        weekday: {
          General: { walking: '$22', cart: '$30', notes: 'Open-4pm' },
          Twilight: { walking: '$14', cart: '$23', notes: '4pm-Close' }
        },
        weekend: {
          General: { walking: '$26', cart: '$35', notes: 'Open-4pm' },
          Twilight: { walking: '$20', cart: '$28', notes: '4pm-Close' }
        },
        senior: {
          weekday: { walking: '$14', cart: '$25', notes: 'Mon-Thur' },
        },
      },
      GeneralNotes: '9 Hole Course | Senior is 60+ | Military Discount is Senior Rates',
      website: 'https://www.indianmountaingolf.com/',
      phoneNumber: '(610) 681-4534',
      googlePlaceId: 'ChIJFSr_7BZaxIkR6UF-wov5W2c',
      courseLength: '3399 yards'
    },
    {
      id: 'terra-greens-golf-course',
      name: 'Terra Greens Golf Course',
      image: '/imgs/terraGreenLogo.webp',
      rating: '3.9/5',
      ratingLink: 'https://www.google.com/search?sca_esv=84546c4646d709ac&sxsrf=AE3TifM9Ff3n70kZ8KJsssMeUGU_tYjaVA:1754795193735&q=terra+greens+golf+course&si=AMgyJEvkVjFQtirYNBhM3ZJIRTaSJ6PxY6y1_6WZHGInbzDnMen-eML8lbCCVpsr8-3wFY7cJLNVEbJfQXmZSl9UP1eFrOV2BbdgIUCbQsPUHXUCh7DQrDnh6WZTDL4YIxSl37qlV3tUnnvX2zzeXKPdm80Hbc1cyQ%3D%3D&sa=X&ved=2ahUKEwjGibTBof-OAxV5MlkFHRBzHq8QrrQLegQIGxAA',
      address: '123 Terragreen Drive, East Stroudsburg, PA 18301',
      town: 'East Stroudsburg',
      holes9: {
        weekday: {
          General: { walking: '$20', cart: '$31', notes: 'Open-3pm' },
          Twilight: { walking: '$17', cart: '$27', notes: '3pm-Close' }
        },
        weekend: {
          General: { walking: '$25', cart: '$35', notes: 'Open-3pm' },
          Twilight: { walking: '$18', cart: '$28', notes: '3pm-Close' }
        },
      },
      holes18: {
        weekday: {
          General: { walking: '$27', cart: '$41', notes: 'Open-3pm' },
          Twilight: { walking: '$24', cart: '$37', notes: '3pm-Close' }
        },
        weekend: {
          General: { walking: '$30', cart: '$45', notes: 'Open-3pm' },
          Twilight: { walking: '$25', cart: '$38', notes: '3pm-Close' }
        },
        junior: {
          weekday: { walking: '$12', cart: '$19', notes: 'Same as Weekend' },
        },
      },
      GeneralNotes: '9 Hole Golf Course',
      website: 'https://terragreens.com/',
      phoneNumber: '(570) 421-0120',
      googlePlaceId: 'ChIJI2xK3IqIxIkR5Xa4L6ZwnVc',
      courseLength: '3130 yards'
    },
    {
      id: 'jack-frost-national-golf-club',
      name: 'Jack Frost National Golf Club',
      image: '/imgs/jackFrosLogo.png',
      rating: '4.4/5',
      ratingLink: 'https://www.google.com/search?sca_esv=ff6e487b06cd8b2f&sxsrf=AE3TifMDsJdnPUsJ1i62U-rh3AZDI494xQ:1754791337356&q=jack+frost+national&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s05evosm69zjF_ZYixJFyA39EAQAruWB2oaNKuZoQ0sjCjxlTcAWIc7qEb_ndRPTzuxEpqjtgAnjn0jK5O5PUyOFPdViVJx1iHVyLvE-PfRU3tIXvw%3D%3D&sa=X&ved=2ahUKEwiss8WSk_-OAxXKGFkFHbgXH6QQrrQLegQIHhAA',
      address: '1 Jack Frost Mountain Rd, Blakeslee, PA 18610',
      town: 'Blakeslee',
      holes18: {
        weekday: {
          General: { cart: '$65', notes: 'Open-4pm' },
          Twilight: { cart: '$39', notes: '4pm-Close' }
        },
        weekend: {
          General: { cart: '$95', notes: 'Open-4pm' },
          Twilight: { cart: '$49', notes: '4pm-Close' }
        },
        senior: {
          weekday: { cart: '$40', notes: 'Mon-Thur' },
        },
        junior: {
          weekday: { cart: '$25', notes: 'After 2pm' },
          weekend: { cart: '$30', notes: 'After 2pm' }
        },
      },
      GeneralNotes: 'Senior is 60+ | Junior is 17 & Under',
      website: 'https://www.jackfrostnational.com/?utm_source=extnet&utm_medium=yext',
      phoneNumber: '(570) 443-2414',
      googlePlaceId: 'ChIJyX1KuB72xIkRbmiD_kTaVck',
      courseLength: '7200 yards'
    },
    {
      id: 'hideaway-hills-golf-club',
      name: 'Hideaway Hills Golf Club',
      image: '/imgs/hideawayHillsLogo.png',
      rating: '4.5/5',
      ratingLink: 'https://www.google.com/search?sca_esv=ff6e487b06cd8b2f&sxsrf=AE3TifPRrpc2iBV3tbWzreYxgeAEa6HWBQ:1754790947176&q=hideaway+hills+golf+club&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s3NVeiHtTyaWuFTzZVbRdK7z5Q04rQ4kXJh1ZdVnXyyPSgPBBFPSLgE2Gu8sOENVovuZqWOzc9NIpLbRPCR2w8_3Z6UCP_1NmL1CWAPE_X0eM_-9LA%3D%3D&sa=X&ved=2ahUKEwi92r7Ykf-OAxUqGVkFHR-cJfgQrrQLegQIGxAA',
      address: '159 Golf Course Rd, Kunkletown, PA 18058',
      town: 'Kunkletown',
      holes18: {
        weekday: {
          General: { cart: '$52', notes: 'Open-4pm' },
          Twilight: { cart: '$38', notes: '4pm-Close' }
        },
        weekend: {
          General: { cart: '$64', notes: 'Open-4pm' },
          Twilight: { cart: '$42', notes: '4pm-Close' }
        },
        senior: {
          weekday: { cart: '$42', notes: 'Mon-Thur' },
        },
      },
      GeneralNotes: 'Senior is 60+',
      website: 'https://hideawaygolf.com/',
      phoneNumber: '(610) 681-6000',
      googlePlaceId: 'ChIJ_a6RsDhaxIkRREw-vubCT_E',
      courseLength: '6933 yards'
    },
    {
      id: 'great-bear-golf-club',
      name: 'Great Bear Golf Club',
      image: '/imgs/greatBearLogo.png',
      rating: '4.4/5',
      ratingLink: 'https://www.google.com/search?sca_esv=ff6e487b06cd8b2f&sxsrf=AE3TifPi7V16h_FKtzuF83-5E5nFNEfXFg:1754790302126&q=great+bear+golf+club&si=AMgyJEsVtO7Zu9YEyquic0WJtZiamUti8WlVIiHVse8gMEYClc_EB0lVlz5zvXReonupI5n6RwMYTMTPoYwBlf-QmA_7fQfSTGxgNjUFkyYwriPk8DECuxEqDuKPcAosykm4VnkI2WkUStp205ZhKPo-KV6B6B2WGg%3D%3D&sa=X&ved=2ahUKEwiI_fOkj_-OAxXdGFkFHe5ePToQrrQLegQIIRAA',
      address: '1 Great Bear Ct, East Stroudsburg, PA 18302',
      town: 'East Stroudsburg',
      holes18: {
        weekday: {
          Morning: { cart: '$58', notes: 'Open-11am' },
          Midday: { cart: '$61', notes: '11am-1pm' },
          Twilight: { cart: '$55', notes: '1pm-Close' },
        },
        weekend: {
          Morning: { cart: '$97', notes: 'Open-11am' },
          Midday: { cart: '$103', notes: '11am-1pm' },
          Twilight: { cart: '$66', notes: '1pm-Close' },
        },
      },
      GeneralNotes: 'Semi-private',
      website: 'https://golfgreatbear.com/',
      phoneNumber: '(570) 223-2000',
      googlePlaceId: 'ChIJ3XygHH-ExIkR9wfO7WVdiQU',
      courseLength: '7025 yards'
    },
    {
      id: 'glen-brook-golf-club',
      name: 'Glen Brook Golf Club',
      image: '/imgs/glenBrookLogo.png',
      rating: '4.4/5',
      ratingLink: 'https://www.google.com/search?sca_esv=ff6e487b06cd8b2f&sxsrf=AE3TifNdzNN0ucrr2OwjPmQNAjo7vhzbNw:1754789289268&q=glen+brook+country+club&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s_hnS9INvkNscZu4_SvxlUGkpZ8WsZBryLBWfW70AM_l-a18Q2u6hGvrbpKDyMT-FrWriwrKCBcxS24xV1i7F1bV-v8eBj5PpN-HExWxN3AEqnO4Zg%3D%3D&sa=X&ved=2ahUKEwjxifjBi_-OAxU-GVkFHS0RAXYQrrQLegQIMhAA',
      address: '1044 Hickory Valley Rd, Stroudsburg, PA 18360',
      town: 'Stroudsburg',
      holes9: {
        weekday: {
          General: { walking: '$15', cart: '$30', notes: 'Open-2pm' },
          Twilight: { walking: '$15', cart: '$25', notes: '2pm-Close' }
        },
        weekend: {
          Midday: { walking: '$15', cart: '$33', notes: 'Noon-2pm' },
          Twilight: { walking: '$15', cart: '$25', notes: '2pm-Close' }
        },
        senior: {
          weekday: { walking: '$10', cart: '$25', notes: 'Same as Weekend | $5 Off Cart After 2pm' },
        },
      },
      holes18: {
        weekday: {
          General: { walking: '$28', cart: '$47', notes: 'Open-2pm' },
          Twilight: { walking: '$28', cart: '$36', notes: '2pm-Close' }
        },
        weekend: {
          General: { cart: '$57', notes: 'Open-2pm' },
          Twilight: { walking: '$28', cart: '$36', notes: '2pm-Close' }
        },
        senior: {
          weekday: { walking: '$20', cart: '$39', notes: 'Open-2pm' },
          weekend: { cart: '$49', notes: 'Open-2pm' }
        },
      },
      GeneralNotes: 'Senior Special: $20 Walking & $28 Cart Available 2pm-Close',
      website: 'https://www.glenbrookgolfclub.com/',
      phoneNumber: '(570) 421-3680',
      googlePlaceId: 'ChIJPZZXuOCJxIkRo3UI3RM0prQ',
      courseLength: '6034 yards'
    },
    {
      id: 'buck-hill-golf-club',
      name: 'Buck Hill Golf Club',
      image: '/imgs/buckHillFallsLogo.png',
      rating: '4.7/5',
      ratingLink: 'https://www.google.com/search?sca_esv=e03d869ac8eda435&sxsrf=AE3TifOY1_62q3NmoLCeS3u9SEtJemz0CQ:1754788269739&q=buck+hill+golf+club&si=AMgyJEuzsz2NflaaWzrzdpjxXXRaJ2hfdMsbe_mSWso6src8s6Nfcf43G410Fo-kvOCfy6wKOldgU69NkeBlzx5jU2GqhBteCKsmx3eZErxow2NOrsVmnO55WeuJhOFMy8OKDBAfoc5UEEGTguHMN9FDVDzgBoTnYg%3D%3D&sa=X&ved=2ahUKEwjn-uTbh_-OAxU3D1kFHWZqCbEQrrQLegQIGxAA',
      address: '357 Golf Dr, Buck Hill Falls, PA 18323',
      town: 'Buck Hill Falls',
      GeneralNotes: 'ONLY OPEN TO PUBLIC BEFORE MEMORIAL DAY & AFTER LABOR DAY | 27 Holes Available(3 9 Hole Courses)',
      website: 'https://www.buckhillfalls.com/public/golf',
      phoneNumber: '(570) 595-7730',
      googlePlaceId: 'ChIJD7J15cCTxIkRsxPFjT6qgkk',
      courseLength: '2823-3239 yards'
    },
    {
      id: 'pocono-hills-golf-course',
      name: 'Pocono Hills Golf Course',
      image: '/imgs/poconoHillsGcLogo.png',
      rating: '4.1/5',
      ratingLink: 'https://www.google.com/search?sca_esv=84546c4646d709ac&sxsrf=AE3TifNviV1t81FXdMpqSA1N0IN22CokXA:1754792982865&q=pocono+hills+golf+course&si=AMgyJEvkVjFQtirYNBhM3ZJIRTaSJ6PxY6y1_6WZHGInbzDnMWR5LU3b1qnH-VQ1_FInTZZRnSIJJGMm56Dd5iqPa30GAI_o68JQHUSyJne4TpMiNs1f8LezWjv-Iwhub18jekA2uWB_jCEk03M7YCX1J-4Gy42GSw%3D%3D&sa=X&ved=2ahUKEwiHqZejmf-OAxW4EFkFHcGDIJAQrrQLegQIKhAA',
      address: '124 Golf Dr, East Stroudsburg, PA 18302',
      town: 'East Stroudsburg',
      GeneralNotes: 'For Tee Times & Daily Rates Call the Clubhouse',
      website: 'https://www.poconohillsgolf.com/',
      phoneNumber: '(800) 335-1113',
      googlePlaceId: 'ChIJzcKGGT2DxIkRmsgkDAAg_8k',
      courseLength: '6174 yards'
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