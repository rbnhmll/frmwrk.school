<template>
  <section>
    <h2 class="h2">Workshops</h2>
    <div class="tabs">
      <button
        v-for="(course, i) in courses"
        :key="i"
        class="btn"
        :class="{ active: activeCourse == course.name }"
        @click="loadCourse(course.name)"
      >
        {{ course.name }} <img :src="course.icon" :alt="course.name" />
      </button>
    </div>
    <div
      class="course"
      v-for="(course, i) in courses"
      :key="i"
      :class="{ active: course.active }"
      v-show="activeCourse == course.name"
    >
      <h3 class="h3" v-if="course.longName">{{ course.longName }}</h3>
      <h3 class="h3" v-else>{{ course.name }}</h3>
      <h3 class="h4">Instructor: {{ course.instructor }}</h3>
      <div class="synopsis" v-if="course.synopsisHTML" v-html="course.synopsisHTML"></div>

      <h3 class="h3">What will I learn?</h3>

      <ul>
        <li v-for="(topic, i) in course.topics" :key="i">
          {{ topic }}
        </li>
      </ul>

      <h2 class="h2">Experience</h2>
      <div class="experience" v-html="course.requisitesHTML"></div>
    </div>
  </section>
</template>

<script>
import logoVue from '@/assets/courseLogos/logo-vue.png';
import logoD3 from '@/assets/courseLogos/logo-d3.png';
import logoShopify from '@/assets/courseLogos/logo-shopify.png';

export default {

  name: 'CourseTopics',
  components: {

  },
  data() {
    return {
      activeCourse: 'Vue',
      courses: {
        Vue: {
          name: 'Vue',
          longName: 'Vue.js: For people who heard React is cool',
          icon: logoVue,
          instructor: 'Robin Hamill',
          synopsisHTML: `
            <h4 class="standout">In this workshop, you will learn the key concepts and techniques to get started using Vue.js</h4>
            <p>Together you will build a fully functional web application using the Vue CDN, as well as the new Vue CLI 3!</p>
            <p>As websites have become more complex and interactive, additional libraries and frameworks have appeared on the scene to help make our code manageable and maintainable.</p>
            <p>One of these libraries is Vue.js: the most starred open source project on Github with over 159k stars, and one of the fastest growing JavaScript libraries in popularity.</p>
          `,
          topics: [
            'What is Vue?',
            'Vue CDN',
            'Vue Devtools',
            'The Vue Instance',
            'Declarative Rendering',
            'Directives',
            'Methods',
            'Event handing',
            'Event modifiers',
            'Component Registration',
            'Props',
            'Vue CLI 3',
            'Single File Components',
            'computed properties',
            'Slots (New!)',
            'Refs (New!)',
            'Filters',
            'Gotchas',
            'Tips & Tricks',
            'More...',
          ],
          requisitesHTML: `
            <p>Participants should be comfortable with <strong>HTML</strong> and <strong>CSS</strong>, and have a fundamental understanding of <strong>JavaScript</strong>, the <strong>terminal</strong>, and <strong>npm</strong>.</p>
            
            <p>Experience with other reactive libraries like <strong>React</strong> or <strong>Angular</strong> is a bonus, but not required.</p>
          `,
        },
        D3: {
          name: 'D3',
          longName: 'D3.js',
          icon: logoD3,
          instructor: 'Trudy MacNabb',
          synopsisHTML: `
            <h4 class="standout">This is a beginner level tutorial for people wanting to learn the basics of Data visualization and d3.js!</h4>
            <p>You'll learn to take JSON data and transform it into a line chart. This video goes through each step thoroughly. From scaling data, to creating the axes, to adding a hover we'll go through the mechanics of each principle in D3 and chart making.</p>
            <p>We'll expand upon our charting skills by taking JSON data and transforming it into a bar chart. At this point the patterns and standards of D3 will really become clear.</p>
            <p>We'll learn more advanced methods of D3 by creating a bubble chart. We'll get to see how powerful D3 can be with regards to mathematical calculations.</p>
            <p>Finally we'll take everything we've learned and add dynamic data and user interaction.</p>
          `,
          topics: [
            'What is D3?',
            'Line Chart',
            'Bar Chart',
            'Bubble Chart',
            'Dynamic Chart',
            'Gotchas',
            'Tips & Tricks',
            'More...',
          ],
          requisitesHTML: `
            <p>Participants should be comfortable with <strong>HTML</strong> and <strong>CSS</strong>, and have a fundamental understanding of <strong>JavaScript</strong>, the <strong>terminal</strong>, and <strong>npm</strong>.</p>
            
            <p>Experience with other libraries like <strong>jQuery</strong> is a bonus, but not required.</p>
          `,
        },
        Shopify: {
          name: 'Shopify',
          longName: 'Shopify for Shop Owners & Project Managers',
          icon: logoShopify,
          instructor: 'Trudy MacNabb & Robin Hamill',
          synopsisHTML: `
            <h4 class="standout">In this workshop, you will learn everything you need to know to run your own online store, or Manage a Shopify Development Project</h4>
            <p>Together we'll explore all the major features of the platform, and identify common patterns for success.</p>
            <p>We'll also take a look at getting the most out of the dashboard, and identifying the defining limitations of the platform.</p>
            <p>By the end of ther workshop, you will know what can and cannot be done on Shopify, and have greater confidence understanding the level of effort involved in creating a store.</p>
          `,
          topics: [
            'What is Shopify?',
            'Dashboard',
            'Orders',
            'Products',
            'Collections',
            'Customers',
            'Alalytics',
            'Marketing',
            'Discounts',
            'Apps',
            'Sales Channels',
            'Code editor & Theme Kit',
            'Gotchas & limitations',
            'Tips & Tricks',
            'More...',
          ],
          requisitesHTML: `
            <p>Participants should have some experience with <strong>Shopify</strong> either as a <strong>Shop Owner</strong> or <strong>Project Manger</strong>, and have a basic understanding or interest in <strong>Ecommerce</strong>. Or <a href="https://www.shopify.com/?ref=rbnhmll&utm_campaign=FRMWRK" target="_blank"
            rel="noopener noreferrer">sign up for a free account</a> and check it out for yourself. No coding experience needed.</p>
            <p>This workshop is focused on getting familar with Shopify as a platform, and not on theme development.</p>
          `,
        },
      },
    };
  },
  methods: {
    loadCourse(name) {
      this.activeCourse = name;
    },
  },
};
</script>

<style scoped lang="stylus">
@import '../styles/_vars'

h2
  text-align center

ul
  display grid
  grid-template-columns repeat(auto-fit, minmax(200px, 1fr))
  padding 0
  margin 0
  grid-gap 15px 50px

  li
    text-transform uppercase
    list-style-image url('../assets/vuejs-brands.svg')
    list-style-position inside
    font-weight bold

.tabs
  display grid
  grid-template-columns repeat(auto-fit, minmax(150px, 1fr))
  grid-gap 10px
  button
    display flex
    align-items center
    justify-content center
    opacity 0.5
    background $white
    color $dark-grey
    padding: 10px 20px;
    transition()
    &.active
      box-shadow()
      opacity 1
      color $white
      background $dark-grey
  img
    margin-left 10px
    max-height 1em

</style>
