<template>
  <div>
    <!-- <div class="courses">
      <span v-for="(course, i) in courses" :key="i">
        <input name="courses" type="checkbox" :id="`${course}_${_uid}`" :value="course">
        <label :for="`${course}_${_uid}`">{{ course }}</label>
      </span>
    </div> -->

    <form
      action="https://tinyletter.com/frmwrk"
      method="post"
      target="popupwindow"
      onsubmit="window.open('https://tinyletter.com/frmwrk', 'popupwindow', 'scrollbars=yes,width=800,height=600');return true"
    >
      <h2 class="h4" v-if="eventDetails.event.isLive">Can't make this one?</h2>
      <h2 class="h5">
        Sign up to be the first to know when the next workshops are announced.
      </h2>
      <div class="grid">
        <div class="input-group">
          <input
            type="text"
            name="email"
            id="tlemail"
            class="required email"
            @input="validateEmail($event)"
          />
          <label for="tlemail">Email Address</label>
          <input type="hidden" value="1" name="embed" />
        </div>
        <input
          type="submit"
          value="Notify me!"
          class="btn"
          :disabled="!validEmail"
        />
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "EmailSignupForm",
  props: {
    eventDetails: Object,
  },
  data() {
    return {
      validEmail: false,
      courses: ["Vue", "D3", "Shopify"],
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

.courses
  display grid
  grid-template-columns repeat(3, 1fr)
  grid-gap 10px
  margin-bottom 1.5rem

  input
    margin-right 1rem

.grid
  display grid
  grid-template-columns 1fr min-content
  grid-gap 10px
  margin-top 10px

  @media screen and (max-width 540px)
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
