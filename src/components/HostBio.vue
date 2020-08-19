<template>
  <section id="bio">
    <h2 class="h2">Meet the Instructors</h2>
    <div class="instructor">
      <div class="description">
        <div class="headshot">
          <img src="@/assets/trudyHeadshotSquare.jpg" alt="Trudy MacNabb headshot" />
        </div>
        <h3 class="h4">
          Trudy MacNabb is a cofounder of
          <a
            href="https://www.upatfive.ca/"
            target="_blank"
            rel="noopener noreferrer"
          >Up at Five</a>, a digital agency that specializes in taking your Shopify site to the next level.
        </h3>
      </div>
      <social-icons
        twitter="https://twitter.com/dear_trudence"
        github="https://github.com/deartrudence"
        web="https://www.upatfive.ca/"
      />
    </div>
    <hr />
    <div class="instructor">
      <div class="description">
        <div class="headshot">
          <img src="@/assets/robinHeadshotSquare.jpg" alt="Robin Hamill headshot" />
        </div>
        <h3 class="h4">
          Robin Hamill is a Shopify Expert and E-commerce consultant specializing in performant and accessible custom themes.
        </h3>
      </div>
      <social-icons
        twitter="https://twitter.com/rbnhmll"
        github="https://github.com/rbnhmll"
        web="https://robinhamill.com"
      />
    </div>
  </section>
</template>

<script>
import SocialIcons from './SocialIcons.vue';

export default {
  name: 'HostBio',
  components: {
    SocialIcons,
  },
};
</script>

<style scoped lang="stylus">
@import '../styles/_vars'

h2
  text-align center

p, .headshot
  text-align center

img
  width 100%
  max-width 150px
  border-radius 50%

.description
  margin-bottom 25px
  display grid
  grid-template-columns 150px 1fr
  align-items center
  justify-content flex-start
  grid-gap 0 50px

  @media screen and (max-width 680px)
    grid-template-columns 1fr

hr
  margin-bottom 3rem
</style>
