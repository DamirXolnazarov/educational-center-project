<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <!-- <RouterLink to="/">Home</RouterLink> -->
  <!-- <RouterLink to="/about">About</RouterLink> -->
  <RouterView />

  <div class="footer flex flex-col items-center justify-between text-white w-[100%] h-[98%]">
    <div class="footer_top text-[23px] text-center">
      <span>Ягона интерактив давлат хизматлари портали </span>
    </div>
    <div class="footer_middle w-[42%] flex flex-row justify-between">
      <ul>
        <li class="text-[20px] font-black">Ёрдам ва кўмак</li>
        <li class="text-[16px]">Кўп бериладиган саволлар</li>
        <li class="text-[16px]">Қўлланмалар</li>
        <li class="text-[16px]">Боғланиш</li>
        <li class="text-[16px]">Қайта алоқа</li>
        <li class="text-[16px]">Саволлар ва таклифлар</li>
        <li class="text-[16px]">Портал харитаси</li>
      </ul>
      <ul>
        <li class="text-[20px] font-black">Портал маълумотлари</li>
        <li class="text-[16px]">Ягона портал миссияси</li>
        <li class="text-[16px]">Янгиликлар</li>
        <li class="text-[16px]">Махфийлик сиёсати</li>
        <li class="text-[16px]">Статистика</li>
      </ul>
    </div>
    <div class="footer_bottom w-[80%] text-center">
      <span> Диққат! Агар сиз матнда хатоликларни аниқласангиз, уларни белгилаб, маъмуриятни хабардор қилиш учун
        Ctrl+Enter тугмаларини босинг
        Материаллардан фойдаланганда my.gov.uzга ҳавола бўлиши шарт. <br>
        © Барча ҳуқуқлар ҳимояланган 2013-2023 </span>
    </div>
  </div>
</template>

<style scoped>
.footer {
  background: url("https://my.gov.uz/img/footer-bg.jpg") no-repeat;
  background-size: auto;
  background-size: cover;
  padding: 80px 15px 105px 15px;
}

.footer_middle ul {
  line-height: 32px;
}
</style>
