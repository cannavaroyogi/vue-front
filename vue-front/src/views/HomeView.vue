<template>
  <div class="home">
    <AppNavbar />
    <div class="container">
      <AppHero />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import AppNavbar from "@/components/AppNavbar.vue";
import AppHero from "@/components/AppHero.vue";

export default {
  name: "HomeView",
  components: {
    AppNavbar,
    AppHero,
  },
};
</script>
