<script>
import { RouterLink } from "vue-router";
import ThemeButton from "../components/ThemeButton.vue";
export default {
  components: {
    ThemeButton,
    RouterLink,
  },
  data() {
    return {
      href: "",
    };
  },
  watch: {
    $route(to) {
      this.href = to.path;
    },
  },
  mounted() {
    this.href = window.location.pathname;
  },
};
</script>
<template>
  <nav>
    <div class="icons-container">
      <router-link to="/">
        <div class="menu-link-container" :class="{ selected: href === '/' }">
          <span class="material-symbols-rounded"> home </span>
        </div>
      </router-link>
      <router-link to="/">
        <div
          class="menu-link-container"
          :class="{ selected: href === '/planning' }"
        >
          <span class="material-symbols-rounded"> list_alt </span>
        </div>
      </router-link>
      <router-link to="/list">
        <div
          class="menu-link-container"
          :class="{ selected: href === '/list' }"
        >
          <span class="material-symbols-rounded"> checklist </span>
        </div>
      </router-link>
      <router-link to="/">
        <div
          class="menu-link-container"
          :class="{ selected: href === '/recipes' }"
        >
          <span class="material-symbols-rounded"> receipt_long </span>
        </div>
      </router-link>
      <router-link to="/">
        <div
          class="menu-link-container"
          :class="{ selected: href === '/user' }"
        >
          <span class="material-symbols-rounded"> person </span>
        </div>
      </router-link>
    </div>
    <div class="theme-button">
      <ThemeButton />
    </div>
  </nav>
</template>
<style scoped>
nav {
  position: fixed;
  top: 0;
  left: 0;
  width: 80px;
  height: 100%;
  padding: 1rem 0 1rem 1rem;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
a,
a:hover {
  color: inherit;
}
.icons-container {
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  gap: 0.5rem;
  overflow: hidden;
}
.menu-link-container {
  width: 100px;
  height: 50px;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  border-radius: 10rem;
}
.theme-button {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}
@keyframes color {
  0% {
    background-color: #fff0;
  }
  100% {
    background-color: #fff4;
  }
}
.menu-link-container:hover {
  background-color: #fff4;
  animation: color 0.5s forwards;
  cursor: pointer;
}
@keyframes bigger {
  0% {
    transform: scale(1);
  }
  100% {
    transform: scale(1.1);
  }
}
.menu-link-container:hover span {
  animation: bigger 0.5s forwards;
}
span {
  font-size: 2rem;
  cursor: pointer;
  margin-right: 30px;
}
[data-theme="dark"] nav {
  background-color: var(--black-secondary);
  color: var(--light);
}
[data-theme="dark"] .selected {
  background-color: var(--light);
  color: var(--black);
}
[data-theme="light"] nav {
  background-color: var(--dark-blue);
  color: var(--light);
}
[data-theme="light"] .selected {
  background-color: var(--light);
  color: var(--dark-blue);
}
.selected:hover,
.selected:hover span {
  animation: none;
}

@media screen and (max-width: 768px) {
  nav {
    position: fixed;
    top: calc(100% - 80px);
    left: 0;
    height: 80px;
    width: 100%;
    padding: 0;
    display: flex;
    flex-direction: row-reverse;
    justify-content: center;
    transform: rotate(180deg);
    overflow: hidden;
  }
  .icons-container {
    padding-bottom: 7rem;
    height: 100%;
    width: fit-content;
    display: flex;
    flex-direction: row-reverse;
    justify-content: center;
    gap: 1rem;
    transform: rotate(180deg);
    overflow: hidden;
  }
  .icons-container span {
    text-align: center;
    margin: 0;
    margin-top: 30px;
  }
  .menu-link-container {
    height: 100px;
    width: 50px;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    border-radius: 10rem;
  }
  .theme-button {
    width: 100px;
    height: 100%;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
  }
}
</style>
