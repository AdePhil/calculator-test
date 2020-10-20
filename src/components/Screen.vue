<template>
  <div class="display">
    <slot></slot>
  </div>
</template>
<style lang="scss" scoped>
.display {
  width: 100%;
  height: 135px;
  border-bottom: 3px solid #ddd;
  text-align: right;
  font-size: 2.2rem;
  padding-top: calc(135px - 5rem);
  padding-right: 2px;
  color: green;
  overflow: hidden;
  background-color: #fff;
}
</style>
