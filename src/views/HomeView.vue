<script setup>
import icon from '../components/iconca.vue'
import loading from '../components/loadingBar.vue'
</script>

<template>
  <div class="home">
     <icon class="icon"/>
     <loading v-if="loadi"/>
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
@media screen and (min-width: 300px) {
  .home {
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    padding-top: 200px;
    align-items: center;
    justify-content: space-between;
    padding-bottom: 150px;
    background-color: #2a2a72;
    background-image: linear-gradient(315deg, #2a2a72 0%, #009ffd 74%);
  }
  .icon{
    animation: 2.5s logo ease-out;
  }
}
</style>
