<template>

  <div class="history element">
      <h6 class="title">შემოთავაზებული</h6>
      <div v-for="(history, index) in historyInfo" :key="index"  class="history__skin" style="display:flex">
         <div class="user-pic">
            <i class="fas fa-user-circle"></i> 
         </div>
         <div class="user-info">
             <h5>{{history.name}}</h5>
             <h5> მობილური {{history.mobile}}</h5>
         </div>
         <i class="fas fa-phone-square call-history" ></i>
      </div>
  </div>
</template>

<script>
export default {
    data() {
        return {
            historyInfo: [
                {
                    icon: '<i class="fas fa-user-circle"></i>',
                    name: 'ამიკო',
                    mobile: 599434599
                },
           
                {
                    icon: '<i class="fas fa-user-circle"></i>',
                    name: 'ამირანი',
                    mobile: 599434599
                },
                {
                    icon: '<i class="fas fa-user-circle"></i>',
                    name: 'გიორგი',
                    mobile: 599434599
                },
                {
                    icon: '<i class="fas fa-user-circle"></i>',
                    name: 'ზურა',
                    mobile: 599434599
                },
                {
                    icon: '<i class="fas fa-user-circle"></i>',
                    name: 'ზურა',
                    mobile: 599434599
                }
                
            ]
        }
    }
}
</script>

<style scoped>
 .history {
     height: 48%;
     width: 100%;
     background-color: #fefefa;
     border-top-left-radius: 15px;
     border-top-right-radius: 15px;
     overflow: auto;
     

 }
::-webkit-scrollbar {
display: none;
}

.history__skin {
    overflow: auto;
    height: 55px;
}

 .title {
     margin-top: 30px;
     margin-left: 15px;
     color: rgba(26, 3, 3, 0.829);
     margin-bottom: 15px;
 }

.call-history {
    margin-left: 30px;
    font-size: 23px;
    margin-top: 7px;
    cursor: pointer;
}

.call-history:hover {
    color: rgba(26, 3, 3, 0.829);
}

 .user-pic {
     margin-left: 20px;
 }

 .user-pic i {
     font-size: 25px;
 }
 
 .user-info h5 {
     margin-left: 10px;
     font-weight: 400;
     color: rgba(26, 3, 3, 0.829);
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