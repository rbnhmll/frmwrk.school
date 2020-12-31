<template>
  <div class="home wrapper">
    <card>
      <v-header :eventDetails="eventDetails" />
    </card>
    <!-- <card>
      <description />
    </card> -->
    <card>
      <course-topics />
    </card>
    <card>
      <host-bio />
    </card>
    <card>
      <event-details :eventDetails="eventDetails" />
    </card>
    <card>
      <email-signup-form :eventDetails="eventDetails" />
    </card>
    <v-footer />
  </div>
</template>

<script>
import Card from '../components/Card.vue';
import VHeader from '../components/VHeader.vue';
import EmailSignupForm from '../components/EmailSignupForm.vue';
import Description from '../components/Description.vue';
import CourseTopics from '../components/CourseTopics.vue';
import EventDetails from '../components/EventDetails.vue';
import HostBio from '../components/HostBio.vue';
import VFooter from '../components/VFooter.vue';

export default {
  name: 'app',
  components: {
    Card,
    VHeader,
    EmailSignupForm,
    Description,
    CourseTopics,
    EventDetails,
    HostBio,
    VFooter,
  },
  data() {
    return {
      eventDetails: {
        event: {
          name: 'Vue.js',
          online: true,
          isLive: true,
          hasEarlyBird: false,
          isSoldOut: false,
          signupLink: 'https://ti.to/frmwrk/vue-js',
          location: {
            TBD: false,
            date: 'Sunday January 24, 2021',
            time: '10am - 2pm (EST)',
          },
        },
        pricing: {
          earlyBird: 200,
          regular: 250,
        },
      },
    };
  },
};
</script>
