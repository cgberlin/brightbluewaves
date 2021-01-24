<!-- Main landing page / displays a listing of posts -->
<template>
  <Layout>
    <section class="projects">
      <!-- 
        iterate through the projects from ./projects 
        click -> ./Project.vue 
      -->
      <article
        @click="goTo($event, project.node.path)"
        class="project"
        v-for="project in $page.projects.edges"
        :key="project.node.id"
      >
        <!-- main post image on landing page -->
        <g-image
          class="project-thumbnail"
          :src="project.node.thumbnail"
          :alt="project.node.title"
        ></g-image>
        <!-- 
          meta data component beneath the image 
        -->
        <ProjectMeta
          :title="project.node.title"
          :categories="project.node.categories"
          :year="project.node.year"
          :author="project.node.author"
        />
      </article>
    </section>
  </Layout>
</template>

<!-- 
Query gridsome for our projects 
These are located at ./projects      
Objects are mapped to $page.projects
-->
<page-query>
query Projects {
  projects: allProject {
    edges {
      node { 
        id
        path
        title
        year
        thumbnail
        categories
        author
      }
    }
  }
}
</page-query>

<script>
import ProjectMeta from "@/components/ProjectMeta";

export default {
  components: {
    ProjectMeta
  },
  metaInfo: {
    titleTemplate: require("../data/theme.json").site_name
  },
  methods: {
    goTo(event, route) {
      const distanceScrolled = window.pageYOffset;
      const elementPosition = event.target.getBoundingClientRect().top;
      const totalOffset = distanceScrolled + elementPosition;
      const finalPosition = totalOffset - 167;

      // Scroll window so that the thumbnail is 12rem from the
      // top of the browser window, this will make a seamless transition.
      window.scrollTo({ top: finalPosition, behavior: "smooth" });

      // Now, navigate to the project page
      setTimeout(() => {
        this.$router.push(route);
      }, 450);
    }
  }
};
</script>

<style lang="scss" scoped>
.projects {
  margin: 0 2rem;
}
.project {
  width: 100%;
  margin-bottom: 4rem;
  cursor: pointer;
}
.project-thumbnail {
  display: block;
  width: 100%;
}
</style>
