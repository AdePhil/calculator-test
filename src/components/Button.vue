<template>
  <button
    :style="{ backgroundColor: bg }"
    :class="`button ${className}`"
    v-bind="$attrs"
  >
    <slot></slot>
    <div class="waveButton"></div>
  </button>
</template>

<script>
export default {
  props: {
    bg: String,
    className: String,
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
  outline: none;
}
.waveButton {
  content: "";
  top: 0%;
  left: 20%;
  background-color: rgba(255, 255, 255, 0.2);
  position: absolute;
  border-radius: 50%;
  width: 4.5rem;
  height: 4.5rem;
  transform: scale(0);
  opacity: 0;
  z-index: 1;
}
@keyframes ripple {
  0% {
    transform: scale(0);
  }
  20% {
    transform: scale(2);
    opacity: 0.5;
  }
  100% {
    transform: scale(2);
    opacity: 0;
  }
}

.ripple {
  animation: ripple 500ms forwards;
}
</style>
