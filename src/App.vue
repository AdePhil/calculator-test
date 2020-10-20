<template>
  <Phone>
    <Screen>{{ lastNumber }}</Screen>
    <div class="expression">{{ value }}</div>
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

      <Button :bg="colors.lightDark" @click="handleClick">7</Button>
      <Button :bg="colors.lightDark" @click="handleClick">8</Button>
      <Button :bg="colors.lightDark" @click="handleClick">9</Button>
      <Button :bg="colors.orange" @click="handleClick">+</Button>

      <Button :bg="colors.lightDark" @click="handleClick">4</Button>
      <Button :bg="colors.lightDark" @click="handleClick">5</Button>
      <Button :bg="colors.lightDark" @click="handleClick">6</Button>
      <Button :bg="colors.orange" @click="handleClick">-</Button>

      <Button :bg="colors.lightDark" @click="handleClick">1</Button>
      <Button :bg="colors.lightDark" @click="handleClick">2</Button>
      <Button :bg="colors.lightDark" @click="handleClick">3</Button>
      <Button :bg="colors.orange" @click="handleClick">*</Button>

      <Button :bg="colors.lightDark" @click="handleClick">0</Button>
      <Button :bg="colors.lightDark" @click="handleClick">.</Button>
      <Button :bg="colors.lightDark" @click="handleClick">&#61;</Button>
      <Button :bg="colors.orange" @click="handleClick">/</Button>
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
      lastNumber: 0,
      value: "",
      colors,
    };
  },
  computed: {
    equal() {
      return this.lastNumber;
    },
  },
  methods: {
    test() {},
    handleClick(e) {
      const text = e.target.innerText;

      if (text != "=" && text != "C" && text != "X") {
        this.value += text;
      } else if (text === "=") {
        this.equals();
      } else if (text === "C" || text === "C") {
        this.clear();
      } else if (text === "X" || text === "X") {
        this.multiply();
      } else if (text === "/") {
        this.divide();
      }
    },
    multiply() {
      this.value += " * ";
    },
    divide() {
      this.value += " / ";
    },
    plus() {
      this.value += " + ";
    },
    minus() {
      this.value += " - ";
    },
    equals() {
      this.value = eval(this.value);
      this.lastNumber = this.value;
    },
    clear() {
      this.value = "";
    },
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
.expression {
  position: absolute;
  top: 0;
  right: 0;
  width: 100%;
  height: 70px;
  font-size: 12px;
}
</style>
