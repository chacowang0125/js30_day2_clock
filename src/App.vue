<template>
  <div id="app">
    <header>JS30 Day2 Clock</header>
    <div class="clock">
      <div class="clock-face">
        <div
          class="hand hour-hand"
          :style="{ transform: `rotate(${this.hourDegrees}deg)` }"
        ></div>
        <div
          class="hand min-hand"
          :style="{ transform: `rotate(${this.minuteDegrees}deg)` }"
        ></div>
        <div
          class="hand second-hand"
          :style="{ transform: `rotate(${this.secondDegrees}deg)` }"
        ></div>
      </div>
    </div>
    <footer>Chaco Wang</footer>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return { secondDegrees: "", minuteDegrees: "", hourDegrees: "" };
  },
  methods: {
    setDate() {
      const now = new Date();
      const second = now.getSeconds();
      this.secondDegrees = (second / 60) * 360 + 90;

      const minute = now.getMinutes();
      this.minuteDegrees = (minute / 60) * 360 + 90;

      const hour = now.getHours();
      this.hourDegrees = (hour / 12) * 360 + 90;
    },
  },
  created() {
    setInterval(this.setDate, 1000);
  },
};
</script>

<style>
html {
  background: url("../src/assets/bgi.jpg");
  background-size: cover;
  font-family: "helvetica neue";
  text-align: center;
  font-size: 10px;
}

body {
  margin: 0;
  font-size: 2rem;
  display: flex;
  flex: 1;
  min-height: 100vh;
  align-items: center;
}
#app {
  width: 100vw;
  height: 100vh;
}
header {
  width: 100%;
  height: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 3.5rem;
  font-family: "Square Peg", cursive;
  letter-spacing: 1rem;
  background-color: rgba(200, 200, 200, 0.3);
}

footer {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100vw;
  height: 2rem;
  position: fixed;
  bottom: 0;
  font-size: 1rem;
  font-weight: 200;
  letter-spacing: 2px;
  color: #fff;
  background-color: rgba(46, 43, 43, 0.7);
}
.clock {
  width: 30rem;
  height: 30rem;
  border: 20px solid white;
  border-radius: 50%;
  margin: 120px auto;
  position: relative;
  padding: 2rem;
  box-shadow: 0 0 0 4px rgba(0, 0, 0, 0.1), inset 0 0 0 3px #efefef,
    inset 0 0 10px black, 0 0 10px rgba(0, 0, 0, 0.2);
}

.clock-face {
  position: relative;
  width: 100%;
  height: 100%;
  transform: translateY(-3px); /* account for the height of the clock hands */
}

.hand {
  width: 50%;
  height: 6px;
  background: black;
  position: absolute;
  top: 50%;
  border-radius: 3px;
  transform: rotate(90deg);
  transform-origin: 100%;
  translate: all 0.05s;
  transition-timing-function: cubic-bezier(0.1, 2.7, 0.58, 1);
}
</style>
