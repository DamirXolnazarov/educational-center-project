<script setup>
import icon from '../components/iconca.vue'
import loading from '../components/loadingBar.vue'
</script>

<template>
  <div class="home">
     <icon class="icon"/>
     <loading v-if="loadi"/>
     <div class="header">
      <div class="oqu"><span>O'qituvchilar uchun</span></div>
      <div class="oqi"><span>O'quvchilar uchun</span></div>
     </div>
  </div>
</template>
<script>
export default {
    data() {
        return {
            loadi: false
        };
    },

    created() {
      setTimeout(() => {
        this.loadi = true
      }, 2000);
      setTimeout(() => {
        let icon = document.querySelector('.icon')
        icon.classList.add('ico')
        this.loadi = false
      }, 5000);
    },

    methods: {
        
    },
};
</script>
<style scoped>
@keyframes logo{
  0%{
    opacity: 0;
  }
  100%{
    opacity: 100%;
  }
}
@keyframes logoPos{
  0%{
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
  }
  100%{
    transform: scale(10%);
    top: 0;
  }
}
@media screen and (min-width: 300px) {
  .home {
    width: 100%;
    height: 100%;
    background-color: #2a2a72;
    display: flex;
    position: relative;
    flex-direction: row;
    align-items: flex-end;
    justify-content: center;
    padding-bottom: 150px;
    background-image: linear-gradient(315deg, #2a2a72 0%, #009ffd 74%);
  }
  .icon{
    transition: .3s;
    animation: 2.5s logo ease-out;
    top: 20%;
    left: 50%;
    transform: translate(-50%);
    position: absolute;
  }
  .ico{
     position: absolute;
     left: 50px;
     transition: .3s;
     top: 0px;
     width: 120px;
     height: 120px;
  }
  .oqu{
    display: flex;
    padding: 7px 12px;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    border: 1px solid white;
    color: white;
    border-radius: 15px;
  }
  .oqi{
    display: flex;
    padding: 7px 12px;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    border: 1px solid white;
    color: white;
    border-radius: 15px;
  }
  .header{
    width: 100%;
    height: 100px;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    position: absolute;
    top: 0;
    align-items: center;
    
  }
}
</style>
