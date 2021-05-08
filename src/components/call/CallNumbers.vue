<template>
   <div class="caller" v-if="isCall">
        <i class="fas fa-user-circle user"></i>  
        <p>{{numbersData}}</p>
         <i class="fas fa-spinner fa-pulse user"></i>
   </div>
   
  <div class="phone-grid element">
    <i class="fas fa-times delete-number" @click="deleteNumber"> </i>
    <div class="line"></div>
    <div class="numbers-data element">{{ numbersData }}</div>
    <div
      v-for="(number, index) in numbers"
      :key="index"
      class="numbers"
      @click="addNumber(number)"
    >
      {{ number }}
    </div>
    <div class="bottom-line"></div>
    <i  class="fas fa-phone-square-alt start-call" @click="calling"></i>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numbers: [1, 2, 3, 4, 5, 6, 7, 8, 9, "*", 0, "#"],
      numbersData: null,
      numbersArray: [],
      isCall: false
    };
  },
  methods: {
    addNumber(number) {
      this.numbersArray.push(number);
      this.numbersData = this.numbersArray.join("");
      
      let sound = new Audio();
      let random = Math.floor(Math.random() * 10);    
      console.log(random)
      if ( random % 2 === 0) {
        
        sound.src = require('../../sounds/2.mp3');
        sound.play();
      }else {
         sound.src = require('../../sounds/3.mp3');
         sound.play();
      }

    },
    calling() {
      if(this.numbersData.length >= 9) {
        this.isCall = true
        let audio = new Audio();
        audio.src = require('../../sounds/zari.mp3')
        audio.loop = true;
        audio.play();
        
        setTimeout(() => {
           audio.pause();
           let newAudio = new Audio()
           newAudio.src = require('../../sounds/gnaxav.mp3')
           newAudio.play();

        }, 4000);
        
        setTimeout(() => {
          this.isCall = false;
        }, 9000);

      }
      
    },
    deleteNumber() {
      this.numbersArray.pop();
        this.numbersData = this.numbersArray.join("");
    }
  },
};
</script>

<style scoped>

.caller {
  position: absolute;
  height: 48%;
  width: 100%;
  background-color: #fefefa;
  border-top-left-radius: 15px;
  border-top-right-radius: 15px;
  
}

.caller p {
  margin-left: 32%;
  font-size: 20px;
  margin-top: 15px;
}

.user {
  font-size: 50px;
  margin-left: 40%;
  margin-top: 20px;
}

.numbers-data {
  position: absolute;
  left: 40px;
  font-size: 25px;
  color: gray;
}

.phone-grid {
  width: 100%;
  
  background-color: #fefefa;
  height: 52%;
  border-bottom-left-radius: 15px;
  border-bottom-right-radius: 15px;
  display: grid;
  grid-auto-rows: 40px;
  grid-template-columns: 1fr 1fr 1fr;
  box-shadow: 0px 0px 5px 0px rgba(0, 0, 0, 0.75);
  position: relative;
}

.numbers {
  margin: 30px;
  font-size: 30px;
  color: #0074D9;
  display: flex;
  justify-content: center;
  cursor: pointer;
}

.numbers:hover {
  color: #2bd900;
}

.start-call {
  position: absolute;
  bottom: 20px;
  cursor: pointer;
  border-radius: 100px;
  left: 44.7%;
  font-size: 35px;
  color: #0074D9 ;
}

.start-call:hover {
 color: #00d9ce ;
}

.line {
  position: absolute;
  border-top: 1px solid rgba(0, 0, 0, 0.541);
  left: 0px;
  width: 100%;
  top: 28px;
}

.delete-number {
  position: absolute;
  right: 5px;
  font-size: 25px;
  cursor: pointer;
  color: gray;
}

.delete-number:hover {
  color: rgba(230, 88, 88, 0.685)
}

.element {
  animation: pulse 2s ;
}

@keyframes pulse {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

</style>