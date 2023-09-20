<template>
  <div class="mainLayout">
    <Header />
    <main class="mainContent">
      <nuxt />
    </main>
  </div>
</template>

<script>
import Header from "~/components/layouts/Header.vue";
export default {
  name: "DefaultLayout",
  components: {
    Header,
  },
};
</script>

<style></style>
