<template>
  <div class="phone">
    <div class="phone__volume"></div>
    <div class="phone__starter"></div>
    <div class="phone__skin">
      <div class="skin__part">
        <div class="part__rect"></div>
        <div class="part__circle"></div>
      </div>
      <div class="info">
        <p>{{ this.time }}</p>
        <i class="fas fa-wifi wifi"></i>

        <i class="fas fa-bolt percentage"></i>
      </div>
      <callHistory v-if="isCall === true" />
      <callNumbers v-if="isCall === true" />

      <div class="phone__buttons" v-if="isCall === false">
        <i @click="goCall" class="fas fa-phone-square-alt call"></i>
        <i class="fas fa-photo-video call"></i>
        <i class="fas fa-calculator call"></i>
      </div>
    </div>
  </div>
</template>

<script>
import callNumbers from "./call/CallNumbers";
import callHistory from "./call/CallHistory";
export default {
  components: {
    callNumbers,
    callHistory,
  },
  data() {
    return {
      isCall: false,
      time: null,
    };
  },
  methods: {
    goCall() {
      this.isCall = true;
    },
  },
  mounted() {
    setInterval(() => {
      let d = new Date();
      let n = d.getHours();
      let m = d.getMinutes();
      this.time = `${n}:${m}`;
    }, 1000);
  },
};
</script>
<style>
* {
  margin: 0;
  padding: 0;
}

.percentage {
  position: absolute;
  right: 25px;
  font-size: 12px;
}

.info {
  position: absolute;
  left: 11px;
  top: 2px;
  display: flex;
  width: 100%;
}
.info p {
  position: fixed;
  font-size: 14px;
  font-weight: 600;
  color: rgba(26, 3, 3, 0.829);
}

.wifi {
  position: absolute;
  right: 43px;
  font-size: 12px;
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

.phone {
  width: 300px;
  border-radius: 25px;

  height: 500px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-top: 9px solid #74777c;
  border-bottom: 9px solid #74777c;
  border-left: 4px solid #74777c;
  border-right: 4px solid #74777c;
  background-color: #74777c;
  position: relative;
}

.phone__volume {
  position: absolute;
  width: 5px;
  height: 60px;
  border-radius: 5px;
  background-color: #74777c;
  left: -7px;
  top: 100px;
}

.phone__starter {
  position: absolute;
  width: 5px;
  height: 40px;
  border-radius: 5px;
  background-color: #74777c;
  left: -7px;
  top: 180px;
}

.phone__skin {
  width: 290px;
  border: 10px solid #303030;
  border-radius: 25px;
  height: 488px;
  position: relative;
  display: flex;
  flex-wrap: wrap;

  background-image: url("../phone-back.jpg");
}

.skin__part {
  position: absolute;
  left: 20%;
  border-radius: 0px 0px 18px 18px;
  width: 170px;
  background-color: #303030;
  height: 18px;
  display: flex;
  justify-content: center;
}

.part__rect {
  width: 60px;
  height: 10px;
  border-radius: 15px;
  background-color: #9498a1;
}

.part__circle {
  width: 10px;
  height: 10px;
  border-radius: 100%;
  background-color: #9498a1;
  margin-left: 10px;
}

.phone__buttons {
  position: absolute;
  width: 95%;
  height: 70px;
  bottom: 10px;
  border-radius: 25px;
  background-color: #55b9e3;
  left: 5px;
  display: flex;
  justify-content: space-around;
}

.call {
  font-size: 40px;
  margin-top: 15px;
  cursor: pointer;
}

/* .call:hover {
    transform: translateY(-50px);
} */
</style>
