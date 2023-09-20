<template>
  <div
    class="baseSwitch"
    :style="{ ...bgBackground, ...fontSize }"
    @mouseup.self="handleSwitch"
  >
    <div
      class="baseSwitch__outline"
      :style="{ ...bgOutline }"
      :class="{ active: value }"
    >
      <div class="baseSwitch__button" :style="{ ...bgButton }"></div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: Boolean,
      default: false,
    },
    bgActiveColor: {
      type: String,
      default: "#409EFF",
    },
    bgInactiveColor: {
      type: String,
      default: "#C0CCDA",
    },
    color: {
      type: String,
      default: "#fafafa",
    },
    outlineGradient: {
      type: String,
      default: "",
    },
    size: {
      type: Number,
      default: 48,
    },
  },
  computed: {
    bgBackground() {
      return {
        backgroundColor: this.value ? this.bgActiveColor : this.bgInactiveColor,
      };
    },
    fontSize() {
      return {
        fontSize: `${this.size}px`,
      };
    },
    bgOutline() {
      return this.outlineGradient
        ? {
            backgroundImage: this.outlineGradient,
          }
        : {
            backgroundColor: this.color,
          };
    },
    bgButton() {
      return {
        backgroundColor: this.color,
      };
    },
  },
  methods: {
    handleSwitch() {
      this.$emit("input", !this.value);
    },
  },
};
</script>

<style lang="scss" scoped>
$circleWidth: calc(40em / 86 - 0.07em);
.baseSwitch {
  aspect-ratio: 86 / 40;
  width: 1em;
  padding: 0.035em;
  border-radius: 0.5 * $circleWidth;
  transition: 0.2s;
  display: inline-block;
  cursor: pointer;
  &__outline {
    aspect-ratio: 1;
    height: $circleWidth;
    border-radius: 50%;
    padding: 0.035em;
    transition: 0.3s;
    transform: translateY(0);
    box-shadow: 0.1rem 0.3rem 0.8rem 0 rgba($color: #000000, $alpha: 0.7);
    &.active {
      transform: translateX(135%);
      box-shadow: -0.1rem 0.3rem 0.8rem 0 rgba($color: #000000, $alpha: 0.7);
    }
  }
  &__button {
    width: 100%;
    aspect-ratio: 1;
    border-radius: 50%;
  }
}
</style>
