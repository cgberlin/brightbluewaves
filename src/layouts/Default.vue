<!-- Main page wrapper, injects the header and footer around everything -->
<template>
  <div class="layout">
    <Header />
    <slot />
    <Footer />
  </div>
</template>

<script>
import Header from "@/components/Header";
import Footer from "@/components/Footer";

export default {
  components: {
    Header,
    Footer
  }
};
</script>

<style lang="scss">
@import url("https://rsms.me/inter/inter.css");
html {
  font-family: "Avenir", sans-serif;
  font-size: 14px;
  font-weight: 500;
  box-sizing: border-box;
}

@supports (font-variation-settings: normal) {
  html {
    font-family: "Avenir", sans-serif;
  }
}

*,
*:before,
*:after {
  box-sizing: inherit;
}
body {
  background-color: #EFEDE7;
  color: #332E3C;
  margin: 0;
  padding: 0;
}
a {
  color: inherit;
  text-decoration: none;
  border-bottom: 1.5px solid transparent;
  padding-bottom: 0.25rem;
  transition: border 0.15s ease;
  &:hover {
    border-bottom: 1.5px solid currentColor;
  }
}

</style>
