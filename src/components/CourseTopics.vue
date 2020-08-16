<template>
  <section>
    <h2 class="h2">Workshops</h2>
    <div class="tabs">
      <button
        v-for="course in courses"
        :key="course"
        class="btn"
        :class="{ active: activeCourse == course.name }"
        @click="loadCourse(course.name)"
      >
        {{ course.name }} <img :src="course.icon" :alt="course.name" />
      </button>
    </div>
    <div
      class="course"
      v-for="course in courses"
      :key="course"
      :class="{ active: course.active }"
      v-show="activeCourse == course.name"
    >
      <h3 class="h2">{{ course.name }}</h3>
      <h3 class="h3">Instructor: {{ course.instructor }}</h3>
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
import logoVue from '@/assets/logo-vue.png';
import logoD3 from '@/assets/logo-d3.png';

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
          icon: logoVue,
          instructor: 'Robin Hamill',
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
          icon: logoD3,
          instructor: 'Trudy MacNabb',
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
  grid-template-columns repeat(auto-fit, minmax(200px, 1fr))
  grid-gap 10px
  button
    display flex
    align-items center
    justify-content center
  button:not(.active)
    opacity 0.5
  img
    margin-left 10px
    max-height 1em

</style>
