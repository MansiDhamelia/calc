<template>
  <div class="main">
    <div class="container">
      <div class="display">
        <div class="history">
          {{ current || "0" }}
          <p id="history"></p>
        </div>
        <div class="result">
          {{ result }}
          <p id="result"></p>
        </div>
      </div>

      <div class="item_container">
        <button class="operator" @click="clear" id="clear">C</button>
        <button class="operator" @click="remove" id="remove">
          <i class="material-icons" style="font-size: 15px">&#xe14a;</i>
        </button>
        <button class="operator" @click="percent" id="%">%</button>
        <button class="operator" @click="append('/')" id="/">/</button>
        <button class="number" @click="append(1)" id="1">1</button>
        <button class="number" @click="append(2)" id="2">2</button>
        <button class="number" @click="append(3)" id="3">3</button>
        <button class="operator" @click="append('*')" id="*">*</button>
        <button class="number" @click="append(4)" id="4">4</button>
        <button class="number" @click="append(5)" id="5">5</button>
        <button class="number" @click="append(6)" id="6">6</button>
        <button class="operator" @click="append('-')" id="-">-</button>
        <button class="number" @click="append(7)" id="7">7</button>
        <button class="number" @click="append(8)" id="8">8</button>
        <button class="number" @click="append(9)" id="9">9</button>
        <button class="operator" @click="append('+')" id="+">+</button>
        <button class="number" @click="append('00')" id="00">00</button>
        <button class="number" @click="append(0)" id="0">0</button>
        <button class="number" @click="dot()" id=".">.</button>
        <button class="operator" @click="equal" id="=">=</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      current: "",
      result: "",
    };
  },
  methods: {
    clear() {
      this.current = "";
      this.result = "";
    },
    remove() {
      if (this.current) {
        this.current = this.current.substr(0, this.current.length - 1);
      }
    },
    percent() {
      this.result = `${parseFloat(this.current) / 100}`;
    },
    append(number) {
      this.current = `${this.current}${number}`;
    },
    dot() {
      if (this.current.indexOf(".") === -1) {
        this.append(".");
      }
    },
    equal() {
      if (this.current != "") {
        this.result = eval(this.current);
        this.current = "";
      } else {
        this.result = "";
      }
    },
  },
};
</script>

<style scoped>
.main {
  font-family: sans-serif;
  display: flex;
  min-height: 100vh;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.container {
  background-color: rgb(235, 235, 235);
  height: 400px;
  width: 250px;
  border-radius: 10px;
  box-shadow: 2px;
  padding: 5px;
}

.display {
  height: 120px;
  display: flex;
  justify-content: center;
  flex-direction: column;
  background-color: white;
  border-radius: 10px;
}
#history {
  text-align: right;
  padding: 10px;
  margin: 5px;
}

#result {
  text-align: right;
  padding: 10px;
  margin: 5px;

  font-size: 30px;
}

.item_container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-content: flex-end;
  padding-top: 5px;
}

.number,
.operator {
  margin: 4px;
  width: 45px;
  height: 45px;
  border-radius: 50%;
  border-width: 0.5px;
  border-color: rgb(190, 195, 199);
  align-items: center;
}
.number,
.operator:hover {
  cursor: pointer;
}

#clear {
  color: red;
}
.operator {
  color: yellowgreen;
  font-size: 15px;
}
button:nth-child(4) {
  font-size: 20px;
}
button:nth-child(8) {
  font-size: 20px;
  text-align: center;
}
button:nth-child(12) {
  font-size: 20px;
}
button:nth-child(16) {
  font-size: 20px;
}
button:nth-child(19) {
  font-size: 20px;
}
button:nth-child(20) {
  font-size: 20px;
}
</style>
