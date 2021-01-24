<!-- Displays the meta data for a project in a header/title form. Used for individual post. -->
<template>
  <section class="project-header">
    <div class="project-title-row">
      <h2 class="project-title project-title-text">{{ title }}</h2>
      <h2 class="project-title project-author-text">{{ author }}</h2>
    </div>
    <time class="project-year" :datetime="year">{{ year }}</time>
  </section>
</template>

<script>
export default {
  // props are passed in from pages/Index.vue
  props: {
    title: {
      type: String,
      required: false,
    },
    year: {
      type: String,
      required: false,
    },
    author: {
      type: String,
      required: false,
    },
  },
};
</script>

<style lang="scss" scoped>
.project-header {
  display: flex;
  padding: 0rem 0;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  line-height: 1.5;
}
.project-title {
  flex: 0 0 40%;
  font-size: 0.75rem;
  margin: 0;
}
.project-author-text {
  font-weight: 500;
}
.project-title-text {
  font-weight: 700;
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