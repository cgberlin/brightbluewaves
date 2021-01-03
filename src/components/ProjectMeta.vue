<template>
  <section class="project-meta">
    <h2 class="project-title">{{ title }}</h2>
    <ul class="project-categories">
      <li
        class="project-category"
        v-for="(category, index) in categories"
        :key="index"
      >
        {{ category }}
      </li>
    </ul>
    <time class="project-year" :datetime="year">{{ year }}</time>
  </section>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: false
    },
    categories: {
      type: Array,
      required: false
    },
    year: {
      type: String,
      required: false
    }
  }
};
</script>

<style lang="scss" scoped>
.project-meta {
  display: flex;
  padding: 0rem 0;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  line-height: 1.5;
}
.project-title {
  flex: 0 0 40%;
  font-size: 0.75rem;
  font-weight: 500;
  margin: 0;
}
.project-categories {
  flex: 0.5;
  font-size: 0.75rem;
  padding: 0;
  margin: 0;
  list-style-type: square;
}
.project-category {
  padding: 0;
  font-size: 0.75rem;
  margin: 0;
}
.project-year {
  flex: 1;
  text-align: right;
  font-size: 0.85rem;
}
</style>