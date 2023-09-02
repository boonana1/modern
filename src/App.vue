<template>
  <header>
    <AppHeader />
  </header>
  <router-view />
  <footer>
    <AppFooter />
  </footer>
</template>

<script>
import AppHeader from "@/components/AppHeader.vue";
import AppFooter from "@/components/AppFooter.vue";
export default {
  components: {
    AppHeader,
    AppFooter
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: var(--font-color);
}

header,
footer {
  display: flex;
  justify-content: center;
  align-content: center;
  text-align: center;
  background-color: #fff;
  color: var(--font-color);
  padding: 10px 0;
}

footer {
  /* background: linear-gradient(0deg, rgba(69, 51, 45, 0.92) 0%, rgba(69, 51, 45, 0.92) 100%), url("@/assets/img/footer-bg.png"), lightgray -31.667px -44.028px / 109.353% 218.092% no-repeat; */
  background: linear-gradient(0deg, rgba(69, 51, 45, 0.32), rgba(69, 51, 45, 0.32)), url("@/assets/img/footer-bg.png");
  background-blend-mode: darken, normal;
  color: #fff;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: left;
  justify-content: center;
  gap: 20px;
}

nav {
  /* padding: 30px; */
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #fff;
}

@media screen and (max-width:1140px) {
  header {
    padding: 0;
  }

  footer {
    padding-bottom: 0;
    gap: 20px;
  }
}

@media screen and (max-width:715px) {
  header {
    padding: 0;
  }
}
</style>
