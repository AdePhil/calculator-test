<template>
  <div>
    <Phone>
      <Screen>{{ lastNumber }}</Screen>
      <div class="expression">{{ value }}</div>
      <div class="buttons">
        <Button :bg="colors.dark" className="span2" @click="handleClick"
          >%</Button
        >
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
    handleClick(e) {
      const text = e.target.innerText;

      //check math functions
      this.checkMathFunctions();

      if (text != "=" && text != "C") {
        this.value += `${text}`;
      } else if (text === "=") {
        this.equals();
      } else if (text === "C" || text === "C") {
        this.clear();
      } else if (text === "X" || text === "X") {
        this.multiply();
      } else if (text === "/") {
        this.divide();
      } else if (text === "%") {
        this.modulus();
      }
    },
    checkMathFunctions() {
      const regex = /^[-0-9]+/g;
      // check if it's a starts with a number
      if (!regex.test(this.value)) {
        this.value = this.lastNumber === 0 ? "" : `${this.lastNumber}`;
      }
    },
    multiply() {
      this.value += "*";
    },
    divide() {
      this.value += "/";
    },
    plus() {
      this.value += "+";
    },
    minus() {
      this.value += "-";
    },
    modulus() {
      this.value += "%";
    },
    equals() {
      try {
        const value = eval(this.value);
        this.value = `${value}`;
        this.lastNumber = this.value;
      } catch (error) {
        console.log("invalid expression");
      }
    },
    clear() {
      this.value = "";
      this.lastNumber = 0;
    },
    sin() {
      try {
        this.checkMathFunctions();
        const value = this.value || 0;
        const text = `sin(${value})`;
        this.lastNumber = Math.sin(eval(value) || 0);
        this.value = text;
      } catch (error) {
        console.log("invalid expression");
      }
    },
    cos() {
      try {
        this.checkMathFunctions();
        const value = this.value || 0;
        const text = `cos(${value})`;
        this.lastNumber = Math.cos(eval(value));
        this.value = text;
      } catch (error) {
        console.log("invalid expression");
      }
    },
    tan() {
      try {
        this.checkMathFunctions();
        const value = this.value || 0;
        const text = `tan(${value})`;
        this.lastNumber = Math.tan(eval(value));
        this.value = text;
      } catch (error) {
        console.log("invalid expression");
      }
    },
    log() {
      try {
        this.checkMathFunctions();
        const value = this.value || 0;
        const text = `log(${value})`;
        this.lastNumber = Math.log10(eval(value));
        this.value = text;
      } catch (error) {
        console.log("invalid expression");
      }
    },
    log2() {
      try {
        this.checkMathFunctions();
        const value = this.value || 0;
        const text = `log2(${value})`;
        this.lastNumber = Math.log2(eval(value));
        this.value = text;
      } catch (error) {
        console.log("invalid expression");
      }
    },
    square() {
      try {
        this.checkMathFunctions();
        const value = this.value || 0;
        const text = `(${value})^2`;
        this.lastNumber = Math.pow(eval(value), 2);
        this.value = text;
      } catch (error) {
        console.log("invalid expression");
      }
    },
    sqrt() {
      try {
        this.checkMathFunctions();
        const value = this.value || 0;
        const text = `√(${value})`;
        this.lastNumber = Math.sqrt(eval(value));
        this.value = text;
      } catch (error) {
        console.log("invalid expression");
      }
    },
    exp() {
      try {
        this.checkMathFunctions();
        const value = this.value || 0;
        const text = `e^(${value})`;
        this.lastNumber = Math.exp(eval(value));
        this.value = text;
      } catch (error) {
        console.log("invalid expression");
      }
    },
    negate() {
      try {
        this.checkMathFunctions();
        const value = this.value || 0;
        this.lastNumber = eval(value) * -1;
        this.value = `${this.lastNumber}`;
      } catch (error) {
        console.log("invalid expression");
      }
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
  font-family: "roboto slab";
  font-weight: normal;
  /* font-family: "Digital-7", sans-serif; */
  padding: 0 8px;
}
</style>
