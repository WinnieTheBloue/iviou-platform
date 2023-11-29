<script>
export default {
  components: {},
  data() {
    return {
      theme: "light",
    };
  },
  methods: {
    toggleTheme() {
      this.theme = this.theme === "light" ? "dark" : "light";
      localStorage.setItem("theme", this.theme);
    },
  },
  watch: {
    theme(newTheme) {
      document.documentElement.setAttribute("data-theme", newTheme);
    },
  },
  mounted() {
    if (localStorage.getItem("theme")) {
      this.theme = localStorage.getItem("theme");
    } else {
      this.theme = window.matchMedia("(prefers-color-scheme: dark)").matches
        ? "dark"
        : "light";
    }
  },
};
</script>
<template>
  <button @click="toggleTheme">
    <span v-if="theme == 'dark'" class="material-symbols-rounded"> light_mode </span>
    <span v-if="theme == 'light'" class="material-symbols-rounded"> dark_mode </span>
  </button>
</template>
<style>
  button {
    background: none !important;
    color: var(--light) !important;
    border: none;
    cursor: pointer;
    outline: none;
    padding: 0;
    width: 100%;
  }
  button:hover {
    scale: 1.1;
  }
</style>