<!-- page header component, always visible -->
<template>
  <header class="header">
    <!-- link home if clicked -->
    <g-link
      to="/"
      tag="h1"
      class="name"
      :class="{ first: data.first_letter_only }"
    >
      <!-- optional param from forestry to toggle single letter -->
      <span
        class="word"
        :class="{ 'first-line': index === 0 && multiLine }"
        v-for="(word, index) in siteName"
        :key="index"
      >
        <span class="first-letter" v-if="data.first_letter_only && word[0]">{{
          word[0]
        }}</span>
        <span class="letter" v-if="data.first_letter_only">{{
          word.slice(1)
        }}</span>
        <span v-if="!data.first_letter_only">{{ word }}</span>
      </span>
    </g-link>
    <div class="contact">
      <a class="link" @click="showContact = !showContact">contact</a>
    </div>
    <!-- contact form for netlify -->
    <form
      netlify
      v-show="showContact"
      name="contact"
      method="POST"
      data-netlify="true"
      class="fixed-contact-form"
    >
      <div class="form-group">
        <input
          type="text"
          class="form-control"
          id="name"
          placeholder="NAME"
          name="name"
          value=""
        />
      </div>

      <div class="form-group">
        <input
          type="email"
          class="form-control"
          id="email"
          placeholder="EMAIL"
          name="email"
          value=""
        />
      </div>

      <textarea
        class="form-control"
        rows="10"
        placeholder="MESSAGE"
        name="message"
      ></textarea>
      <div class="form-button-container">
        <button class="form-button" id="submit" type="submit">Send</button>
      </div>
    </form>
  </header>
</template>

<script>
import data from "@/data/theme.json";

export default {
  name: "Header",
  data() {
    return {
      data,
      // for toggling the contact form
      showContact: false,
    };
  },
  computed: {
    siteName() {
      return data.header_title.split(" ");
    },
    multiLine() {
      return this.siteName.length >= 1;
    },
  },
};
</script>

<style lang="scss" scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  padding: 4rem 2rem 5rem 2rem;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  z-index: 100;
  opacity: 1;
  transition: opacity 0.5s ease;
  &.hidden {
    opacity: 0;
  }
}
.name {
  font-size: 3rem;
  font-weight: 500;
  user-select: none;
  margin: 0;
  cursor: pointer;
  .word {
    margin-right: 0.5rem;
    &.first-line {
      display: block;
      margin-bottom: 0.5rem;
    }
    &:last-of-type {
      margin: 0;
    }
  }
  &.first {
    .letter {
      transition: opacity 0.15s ease;
      opacity: 0;
    }
    .first-letter {
      opacity: 1;
    }
    &:hover {
      .letter {
        opacity: 1;
      }
    }
  }
}
.contact:hover,
.form-button:hover {
  cursor: pointer;
}
.fixed-contact-form {
  width: auto;
  position: absolute;
  right: 2%;
  top: 20%;
  background: white;
  border-radius: 2%;
  padding: 1rem;
  box-shadow: -1px 2px 4px rgba(0, 0, 0, 0.25), 1px 1px 3px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-flow: column;
}
.form-control,
textarea {
  max-width: 15rem;
  min-width: 15rem;
  width: 15rem;
  margin-top: 0.5rem;
  font-weight: 500;
}
.form-button {
  width: 45%;
}
.form-button-container {
  display: flex;
  flex-flow: row;
  align-items: center;
  justify-content: space-between;
  margin-top: 0.5rem;
}
</style>