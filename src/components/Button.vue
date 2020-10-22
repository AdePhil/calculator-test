<template>
  <button
    :style="{ backgroundColor: bg }"
    :class="`button ${className}`"
    v-bind="$attrs"
    @mousedown="addRipple"
  >
    <slot></slot>
    <div
      :class="{ ripple: hasRipple, waveButton: true }"
      ref="waveButton"
    ></div>
  </button>
</template>

<script>
export default {
  props: {
    bg: String,
    className: String,
  },
  data() {
    return {
      hasRipple: false,
    };
  },
  watch: {
    hasRipple(value) {
      if (value) {
        setTimeout(() => {
          this.hasRipple = false;
        }, 300);
      }
    },
  },
  methods: {
    addRipple() {
      this.hasRipple = true;
    },
  },
};
</script>

<style lang="scss" scoped>
.button {
  display: block;
  height: 4.5rem;
  padding-bottom: 5px;
  padding-top: 5px;
  cursor: pointer;
  transition: 1s ease;
  position: relative;
  color: #fff;
  border: none;
  font-family: "roboto slab";
  font-size: 1.6rem;
  outline: none;
  transition: background-color 300ms ease;
}

.waveButton {
  content: "";
  top: 50%;
  left: 50%;
  background-color: rgba(255, 255, 255, 0.2);
  position: absolute;
  border-radius: 50%;
  width: 4rem;
  height: 4rem;
  transform: scale(0);
  opacity: 0;
  z-index: 1;
  margin: -2rem -2rem;
}
@keyframes ripple {
  0% {
    transform: scale(0);
  }
  20% {
    transform: scale(1.5);
    opacity: 0.5;
  }
  100% {
    transform: scale(1.5);
    opacity: 0;
  }
}

.ripple {
  animation: ripple 500ms forwards;
}
</style>
