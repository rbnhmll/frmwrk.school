<form
  action="https://buttondown.email/api/emails/embed-subscribe/FRMWRK.school"
  method="post"
  target="popupwindow"
  onsubmit="window.open('https://buttondown.email/FRMWRK.school', 'popupwindow')"
  class="embeddable-buttondown-form"
>
  <label for="bd-email">Enter your email</label>
  <input type="email" name="email" id="bd-email"></input>
  <input type="hidden" value="1" name="embed"></input>
  <input type="submit" value="Subscribe"></input>
  <p>
    <a href="https://buttondown.email" target="_blank">Powered by Buttondown.</a>
  </p>
</form>

<template>
  <div id="mc_embed_signup" class="mc_embed_signup">
    <form
      action="https://buttondown.email/api/emails/embed-subscribe/FRMWRK.school"
      method="post"
      id="subscribe-form"
      name="subscribe-form"
      class="validate"
      rel="noopener noreferrer"
      novalidate
    >
      <div id="mc_embed_signup_scroll">
        <h2 class="h4" v-if="eventDetails.event.isLive">Can't make this one?</h2>
        <h2 class="h5">Sign up to be the first to know when the next workshop is announced!</h2>
        <div class="grid">
          <div class="input-group">
            <input
              type="email"
              value=""
              name="email"
              class="required email"
              id="email"
              required
              @input="validateEmail($event)"
            >
            <label for="email">Email Address </label>
          </div>
          <input
            type="submit"
            value="Notify me!"
            name="subscribe"
            class="btn"
            :disabled="!validEmail"
          >
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'EmailSignupForm',
  props: {
    eventDetails: Object,
  },
  data() {
    return {
      validEmail: false,
    };
  },
  methods: {
    validateEmail(e) {
      const email = e.target.value;
      const re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      const result = re.test(email);
      this.validEmail = result;
    },
  },
};
</script>

<style scoped lang="stylus">
@import '../styles/_vars'

.grid
  display grid
  grid-template-columns 1fr min-content
  grid-gap 10px

  @media screen and (max-width: 540px)
    grid-template-columns 1fr

.mc_embed_signup
  display flex
  justify-content center
  text-align center

h2
  // font-size 1em

.input-group
  position relative

  label
    color $dark-grey
    position absolute
    left 1.8rem
    top 50%
    transform translateY(-50%)
    background rgba(255, 255, 225, 0)
    border-radius 3px
    padding 0 5px
    transition all 0.3s

  input
    display block
    width 100%
    padding 15px
    border none
    border-radius 3px
    border 2px solid $dark-grey

    &:hover, &:focus, &:valid
      & + label
        top 0
        background rgba(255, 255, 255, 1)
        font-size 1.6rem
</style>
