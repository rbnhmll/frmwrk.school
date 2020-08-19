<template>
  <ul>
    <li>
      <a :href="web" aria-label="Website" title="Website" target="_blank" rel="noopener noreferrer">
        <icon-website />
      </a>
    </li>
    <li>
      <a
        :href="github"
        aria-label="Github"
        title="Github"
        target="_blank"
        rel="noopener noreferrer"
      >
        <icon-github />
      </a>
    </li>
    <li>
      <a
        :href="twitter"
        aria-label="Twitter"
        title="Twitter"
        target="_blank"
        rel="noopener noreferrer"
      >
        <icon-twitter />
      </a>
    </li>
  </ul>
</template>

<script>
import IconTwitter from './icons/IconTwitter.vue';
import IconGithub from './icons/IconGithub.vue';
import IconWebsite from './icons/IconWebsite.vue';

export default {
  name: 'SocialIcons',
  components: {
    IconTwitter,
    IconGithub,
    IconWebsite,
  },
  props: {
    twitter: String,
    github: String,
    web: String,
  },
};
</script>

<style scoped lang="stylus">
ul
  padding 0
  list-style-type none
  display flex
  justify-content space-between
  width 4em
  margin 25px auto

svg
  height 1em
</style>
