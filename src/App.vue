<template>
  <Phone>
    <Screen>0</Screen>
    <div class="expression"></div>
    <div class="buttons">
      <Button :bg="colors.dark" className="span2" @click="test">CE</Button>
      <Button :bg="colors.dark">C</Button>
      <Button :bg="colors.dark">-M</Button>

      <Button :bg="colors.dark">Sin</Button>
      <Button :bg="colors.dark">Cos</Button>
      <Button :bg="colors.dark">tan</Button>

      <Button :bg="colors.dark">exp</Button>
      <Button :bg="colors.dark">log</Button>
      <Button :bg="colors.dark">log <sub>2</sub></Button>

      <Button :bg="colors.dark"> x<sup>2</sup></Button>
      <Button :bg="colors.dark">&#8730;x</Button>

      <Button :bg="colors.lightDark">7</Button>
      <Button :bg="colors.lightDark">8</Button>
      <Button :bg="colors.lightDark">9</Button>
      <Button :bg="colors.orange">+</Button>

      <Button :bg="colors.lightDark">4</Button>
      <Button :bg="colors.lightDark">5</Button>
      <Button :bg="colors.lightDark">6</Button>
      <Button :bg="colors.orange">-</Button>

      <Button :bg="colors.lightDark">1</Button>
      <Button :bg="colors.lightDark">2</Button>
      <Button :bg="colors.lightDark">3</Button>
      <Button :bg="colors.orange">*</Button>

      <Button :bg="colors.lightDark">0</Button>
      <Button :bg="colors.lightDark">.</Button>
      <Button :bg="colors.lightDark">&#61;</Button>
      <Button :bg="colors.orange">/</Button>
    </div>
  </Phone>
</template>

<script>
import Phone from "./components/Phone";
import Screen from "./components/Screen";
import Button from "./components/Button";
import { colors } from "./constants/colors";

export default {
  name: "App",
  components: {
    Phone,
    Screen,
    Button,
  },
  data() {
    return {
      colors,
    };
  },
  methods: {
    test() {},
  },
};
</script>

<style>
html {
  box-sizing: border-box;
}
*,
*:before,
*:after {
  box-sizing: inherit;
}
html {
  font-size: 62.5%;
}
body {
  font-size: 1.6rem;
  line-height: 1.6;
  background-color: #ffc600;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  font-family: "roboto slab";
}
.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
}
.span2 {
  grid-column: 1 / span 2;
}
</style>
