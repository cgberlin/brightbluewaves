<!-- footer component, always visible -->
<template>
  <footer class="footer">
    <!-- image to link to the top -->
    <div class="to-top" @click="scrollTopTop">
      <img
        class="to-top-image"
        @click="scrollTopTop"
        src="https://lucianet.s3.amazonaws.com/up-arrow.svg"
      />
    </div>
    <p class="copyright-text">&copy; Copyright 2021 brightbluewaves.com</p>

    <!-- show social link if it exists -- removed for now
    <div class="social">
      <a
        class="channel"
        v-for="(social, index) in data.social"
        :key="index"
        :href="`https://${social.channel}.com/${social.handle}`"
      >
        {{ social.link_text }}
      </a>
    </div>
    -->
  </footer>
</template>

<script>
import data from "@/data/theme.json";

export default {
  data() {
    return {
      data,
    };
  },
  methods: {
    scrollTopTop() {
      window.scrollTo({
        top: 0,
        behavior: "smooth",
      });
    },
  },
};
</script>

<style lang="scss">
.footer {
  position: fixed;
  bottom: 0rem;
  left: 0;
  width: 100%;
  display: flex;
  flex-flow: row;
  justify-content: space-between;
  align-items: center;
  padding-top: 1rem;
  padding-bottom: 1rem;
  z-index: 9999;
}
.to-top {
  cursor: pointer;
  bottom: 0;
}
.to-top-image {
  height: auto;
  width: 2rem;
  margin: 0;
}
.copyright-text {
  transform: rotate(90deg);
  padding-bottom: 16rem;
}
.social {
  .channel {
    margin-right: 1rem;
    text-transform: uppercase;
    letter-spacing: 0.05em;
    &:last-of-type {
      margin: 0;
    }
  }
}
</style>