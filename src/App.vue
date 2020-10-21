<template>
  <div>
    <Phone>
      <Screen>{{ lastNumber }}</Screen>
      <div class="expression">{{ value }}</div>
      <div class="buttons">
        <Button :bg="colors.dark" className="span2" @click="test">CE</Button>
        <Button :bg="colors.dark" @click="clear">C</Button>
        <Button :bg="colors.dark" @click="negate">-M</Button>

        <Button :bg="colors.dark" @click="sin">Sin</Button>
        <Button :bg="colors.dark" @click="cos">Cos</Button>
        <Button :bg="colors.dark" @click="tan">tan</Button>

        <Button :bg="colors.dark" @click="exp">exp</Button>
        <Button :bg="colors.dark" @click="log">log</Button>
        <Button :bg="colors.dark" @click="log2">log <sub>2</sub></Button>

        <Button :bg="colors.dark" @click="square"> x<sup>2</sup></Button>
        <Button :bg="colors.dark" @click="sqrt">&#8730;x</Button>

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
  </div>
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
      //don't allow two decimal points

      //check math functions
      this.checkMathFunctions();
      if (text != "=" && text != "C") {
        console.log("here", this.value + `${text}`);
        this.value += `${text}`;
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
    checkMathFunctions() {
      // const regex = /^[a-z]*/i;
      if (
        this.value.startsWith("c") ||
        this.value.startsWith("s") ||
        this.value.startsWith("c") ||
        this.value.startsWith("t") ||
        this.value.startsWith("l") ||
        this.value.startsWith("√") ||
        this.value.startsWith("(") ||
        this.value.startsWith("e")
      ) {
        this.value = this.lastNumber === 0 ? "" : `${this.lastNumber}`;
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
      this.value = `${eval(this.value)}`;
      this.lastNumber = this.value;
    },
    clear() {
      this.value = "";
      this.lastNumber = 0;
    },
    sin() {
      this.checkMathFunctions();
      const value = this.value || 0;
      const text = `sin(${value})`;
      this.lastNumber = Math.sin(eval(value) || 0);
      this.value = text;
    },
    cos() {
      this.checkMathFunctions();
      const value = this.value || 0;
      const text = `cos(${value})`;
      this.lastNumber = Math.cos(eval(value));
      this.value = text;
    },
    tan() {
      this.checkMathFunctions();
      const text = `tan(${this.value})`;
      this.lastNumber = Math.tan(eval(this.value));
      this.value = text;
    },
    log() {
      this.checkMathFunctions();
      const value = this.value || 0;
      const text = `log(${value})`;
      this.lastNumber = Math.log10(eval(value));
      this.value = text;
    },
    log2() {
      this.checkMathFunctions();
      const value = this.value || 0;
      const text = `log2(${value})`;
      this.lastNumber = Math.log2(eval(value));
      this.value = text;
    },
    square() {
      this.checkMathFunctions();
      const value = this.value || 0;
      const text = `(${value})^2`;
      this.lastNumber = Math.pow(eval(value), 2);
      this.value = text;
    },
    sqrt() {
      this.checkMathFunctions();
      const value = this.value || 0;
      const text = `√(${value})`;
      this.lastNumber = Math.sqrt(eval(value));
      this.value = text;
    },
    exp() {
      this.checkMathFunctions();
      const value = this.value || 0;
      const text = `e^(${value})`;
      this.lastNumber = Math.exp(eval(value));
      this.value = text;
    },
    negate() {
      this.checkMathFunctions();
      const value = this.value || 0;
      this.lastNumber = eval(value) * -1;
      this.value = `${this.lastNumber}`;
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
  background-color: #fff;
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
