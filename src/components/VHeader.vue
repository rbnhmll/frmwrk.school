<template>
  <header>
    <h1 class="h1">
      <img alt="FRMWRK School Logo" src="../assets/logo_big.png">
    </h1>
    <h2 class="h3">Live Online workshops to extend your skillset, career and mind</h2>
    <date-location :eventDetails="eventDetails" />
    <SoldOut v-if="eventDetails.event.isSoldOut" />
    <component :is="ctaComp" :eventDetails="eventDetails" />
  </header>
</template>

<script>
import DateLocation from './DateLocation.vue';
import Signup from './Signup.vue';
import EmailSignupForm from './EmailSignupForm.vue';
import SoldOut from './SoldOut.vue';

export default {
  name: 'VHeader',
  components: {
    DateLocation,
    Signup,
    EmailSignupForm,
    SoldOut,
  },
  props: {
    eventDetails: Object,
  },
  computed: {
    ctaComp() {
      return this.eventDetails.event.isLive ? Signup : EmailSignupForm;
    },
  },
};
</script>

<style scoped lang="stylus">
header
  text-align center

img
  max-width 350px
  width 100%

  @media screen and (max-width 480px)
    max-width 200px
</style>
