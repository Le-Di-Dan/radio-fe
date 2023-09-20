<template>
  <header class="mainHeader">
    <div class="mainHeader__logo">Hiep’s Radio</div>
    <div class="mainHeader__switch">
      <span class="switch__text">Power</span>
      <BaseSwitch
        v-model="powerOn"
        :size="86"
        outlineGradient="linear-gradient(to bottom, #ECECEC, #858585)"
        color="#FFFFFF"
        bg-active-color="#F7E92B"
      />
    </div>
  </header>
</template>

<script>
import BaseSwitch from "~/components/common/BaseSwitch.vue";

export default {
  name: "MainHeader",
  components: {
    BaseSwitch,
  },
  data() {
    return {
      powerOn: false,
    };
  },
};
</script>

<style></style>
