<script setup>
import Logo from '../components/logo.vue'
import Card from '../components/cardOfJobs.vue'
import axios from 'axios';
</script>

<template>
  <div class="home">
    <div class="header h-[102px] flex flex-row justify-between w-[100%] bg-[white] px-[155px]">
      <Logo />
      <div class="informs flex flex-row">
        <div class="suggestions h-[102px] flex flex-col justify-center">
          <div class="numbers flex flex-row w-[300px] text-[14px]">
            <span class="number1 w-[140px]">
              <b class="font-black text-[16px]">1242</b> <br>
              my.gov.uz <br> умумий саволлар (24/7)
            </span>
            <span class="number2 w-[100px]">
              <b class="font-black text-[18px]">1148</b> <br>
              таклиф ва шикоятлар
            </span>
          </div>
          <div class="numbers_logo w-[230px] flex flex-row justify-between items-center">
            <div class="line w-[27px] h-[2px] bg-[#C1C1C1]"></div>
            <div class="n_logo flex flex-row items-center justify-between w-[112px]">
              <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="15.847"
                height="13.222" viewBox="0 0 15.847 13.222">
                <defs>
                  <linearGradient id="linear-gradient" x1="0.5" x2="0.5" y2="1" gradientUnits="objectBoundingBox">
                    <stop offset="0" stop-color="#00acaf" />
                    <stop offset="1" stop-color="#009baa" />
                  </linearGradient>
                </defs>
                <path id="headset"
                  d="M3.31,15.222A1.322,1.322,0,0,0,4.633,13.9V9.933A1.322,1.322,0,0,0,3.31,8.611V7.95a4.628,4.628,0,0,1,9.255,0v.661a1.322,1.322,0,0,0-1.322,1.322V13.9H9.26a.661.661,0,0,0,0,1.322h3.305a3.305,3.305,0,0,0,1.322-6.331V7.95a5.95,5.95,0,0,0-11.9,0v.941A3.305,3.305,0,0,0,3.31,15.222Z"
                  transform="translate(-0.014 -2)" fill="url(#linear-gradient)" />
              </svg>
              <span class="font-black text-[15px]">Call-center</span>
            </div>
            <div class="line w-[27px] h-[2px] bg-[#C1C1C1]"></div>
          </div>
        </div>
        <div class="check h-[80px] flex flex-row">
          <div class="w-[140px] pt-[12px] arizaCheck hover:border-b-2">
            <span class="ariz">Ариза холатини текшириш</span>
          </div>
          <div class="aloqa pt-[12px] w-[120px] flex flex-row justify-center">
            <svg class="cursor-pointer" @click="AloqaListShow()" xmlns="http://www.w3.org/2000/svg"
              xmlns:xlink="http://www.w3.org/1999/xlink" width="47" height="47" viewBox="0 0 47 47">
              <defs>
                <linearGradient id="linear-gradient" x1="0.5" x2="0.5" y2="1" gradientUnits="objectBoundingBox">
                  <stop offset="0" stop-color="#00acaf" />
                  <stop offset="1" stop-color="#009baa" />
                </linearGradient>
              </defs>
              <g id="iconH" transform="translate(-1511 112)">
                <circle id="Эллипс_5" data-name="Эллипс 5" cx="23.5" cy="23.5" r="23.5" transform="translate(1511 -112)"
                  fill="url(#linear-gradient)" />
                <path id="megaphone_3_" data-name="megaphone (3)"
                  d="M23,16a1,1,0,0,1-.446-.1l-2-1a1,1,0,1,1,.894-1.79l2,1A1,1,0,0,1,23,16ZM21.447,6.9l2-1a1,1,0,0,0-.894-1.79l-2,1a1,1,0,1,0,.894,1.79ZM24,10a1,1,0,0,0-1-1H21a1,1,0,0,0,0,2h2A1,1,0,0,0,24,10Zm-6,9V1a1,1,0,0,0-2,0c0,2.949-2.583,4-5,4H4A4,4,0,0,0,0,9v2a4,4,0,0,0,4,4h7c2.417,0,5,1.051,5,4a1,1,0,0,0,2,0ZM8.186,17H4a6,6,0,0,1-1.382-.167l2.5,5.582A2.671,2.671,0,0,0,7.558,24,2.462,2.462,0,0,0,9.8,20.528Z"
                  transform="translate(1523 -100)" fill="#fff" />
              </g>
            </svg>
            <div class="dropDownforAloqa absolute w-[170px] top-[80px] h-[100px] pl-[10px] pt-[5px] pb-[5px]"
              v-if="aloqaSelect">
              <img class="absolute top-[-10px] left-[45%]"
                src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABUAAAAKCAYAAABblxXYAAABT0lEQVQoU2NkIAAuX74sy8HBsZifn9/048ePp3/8+BGrq6v7GJ82RnySd+/eVfv///9SSUlJEy4uLoZv374xPH/+/AwjI2O0srLyLVx6cRp69epVLTY2tmVSUlL6IANhAGTws2fPLv769StKW1v7GjaDsRoKNNAA6OUV0tLS6uzs7Bj6fv78yfD06dObwKCIABp8AV0BhqHAMLTi5uZeCnShAjYDYQaADAa6+MHXr1+jgWF8DNlgFENv3LjhCDRoIdCFsqysrITikOH3798gFz8GWhCvoaGxH6YBbuj169fdgV4GGShOjIEwA6AGvwQGRbympuZOkDjYUKCBwZycnHOABgqwsLAQdCG6gj9//oBc/OH79+8pQIPXMgIjJYmHh2cCMAx5yTEQZgHIYGAYf/7y5UsBIzAtzldQUIhkYmL6S7IT0TT8+/eP+cGDB8sBvJyOImVWfdgAAAAASUVORK5CYII="
                alt="">
              <div class="list1 flex flex-col font-thin">
                <span class="px-[10px] hover:bg-[#0082c9] hover:text-white">Telegram канал</span>
                <span class="px-[10px] hover:bg-[#0082c9] hover:text-white">Қайта алоқа</span>
                <span class="px-[10px] hover:bg-[#0082c9] hover:text-white">Telegram чат-бот</span>
                <span class="px-[10px] hover:bg-[#0082c9] hover:text-white">Youtube сахифаси</span>
              </div>
            </div>
          </div>
          <div class="lang relative flex flex-row justify-center items-center">
            <div class="cursor-pointer langSelected" @click="langListShow()">
              <span>УЗ <div class="caret"></div></span>
            </div>
            <div class="dropDownforLang absolute w-[170px] left-[-120px] top-[60px] h-[100px] pl-[10px] pt-[5px] pb-[5px]"
              v-if="langSelect">
              <img class="absolute top-[-10px] left-[75%]"
                src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABUAAAAKCAYAAABblxXYAAABT0lEQVQoU2NkIAAuX74sy8HBsZifn9/048ePp3/8+BGrq6v7GJ82RnySd+/eVfv///9SSUlJEy4uLoZv374xPH/+/AwjI2O0srLyLVx6cRp69epVLTY2tmVSUlL6IANhAGTws2fPLv769StKW1v7GjaDsRoKNNAA6OUV0tLS6uzs7Bj6fv78yfD06dObwKCIABp8AV0BhqHAMLTi5uZeCnShAjYDYQaADAa6+MHXr1+jgWF8DNlgFENv3LjhCDRoIdCFsqysrITikOH3798gFz8GWhCvoaGxH6YBbuj169fdgV4GGShOjIEwA6AGvwQGRbympuZOkDjYUKCBwZycnHOABgqwsLAQdCG6gj9//oBc/OH79+8pQIPXMgIjJYmHh2cCMAx5yTEQZgHIYGAYf/7y5UsBIzAtzldQUIhkYmL6S7IT0TT8+/eP+cGDB8sBvJyOImVWfdgAAAAASUVORK5CYII="
                alt="">
              <div class="list flex flex-col font-thin">
                <span class="px-[15px] hover:bg-[#0082c9] hover:text-white">УЗБЕКЧА</span>
                <span class="px-[15px] hover:bg-[#0082c9] hover:text-white">O'ZBEKCHA</span>
                <span class="px-[15px] hover:bg-[#0082c9] hover:text-white">РУССКЫЙ</span>
                <span class="px-[15px] hover:bg-[#0082c9] hover:text-white">ENGLISH</span>
              </div>
            </div>
          </div>
        </div>

      </div>
    </div>
    <div class="banner w-[100%] px-[155px] flex flex-row justify-between">
      <div class="left_banner w-[500px] flex flex-col justify-between h-[250px] pt-[70px]">
        <span class="text-white text-[25px] font-thin">Ягона интерактив давлат хизматлари порталига хуш келибсиз!</span>
        <div class="btns">
          <button
            class="btn_enter mr-[15px] px-[65px] py-[10px] bg-[white] border-2 rounded-[10px] text-[#1c3a5e] font-black transition-[0.3s] hover:bg-[transparent] hover:text-white">
            Кириш
          </button>
          <button
            class="btn_register px-[45px] py-[10px] border-2 border-white rounded-[10px] text-[white] font-black transition-[0.3s] hover:bg-[white] hover:text-[#1c3a5e]">
            Руйхатдан утиш
          </button>
        </div>
        <span class="text-white underline">
          <RouterLink to="#">Логин ёки паролни унутдингизми?</RouterLink>
        </span>
      </div>
      <div class="right_banner w-[650px] relative flex flex-col justify-between h-[250px] pt-[84px]">
        <div class="top_right_banner w-[700px] flex flex-row">
          <div class="input mr-[15px]">
            <input class="w-[400px] relative rounded-[7px] h-[45px] bg-[white] text-[16px] pr-[45px] pl-[25px] inp"
              :placeholder="currentPlaceholder" />
            <button
              class="bg-[#e1e1e1] text-[#111d2d] rounded-[5px] w-[80px] h-[45px] absolute left-[320px] font-black">Излаш</button>
          </div>
          <div
            class="service_btn cursor-pointer text-white flex flex-row items-center justify-between px-[20px] w-[220px] border-2 border-white rounded-[11px] font-[600] pt-[7px] pb-[9px]">
            Барча хизматлар <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="white"
              class="bi bi-chevron-right" viewBox="0 0 16 16">
              <path fill-rule="evenodd"
                d="M4.646 1.646a.5.5 0 0 1 .708 0l6 6a.5.5 0 0 1 0 .708l-6 6a.5.5 0 0 1-.708-.708L10.293 8 4.646 2.354a.5.5 0 0 1 0-.708z" />
            </svg>
          </div>
        </div>
        <div class="bottom_right_banner">
          <div class="services text-white justify-between flex flex-row w-[450px]">
            <div
              class="firstService w-[200px] h-[100px] flex flex-row justify-between items-center hover:underline cursor-pointer">
              <span>Янги хизмат</span>
              <svg xmlns="http://www.w3.org/2000/svg" width="35" height="35" fill="white" class="bi bi-chevron-right"
                viewBox="0 0 16 16">
                <path fill-rule="evenodd"
                  d="M4.646 1.646a.5.5 0 0 1 .708 0l6 6a.5.5 0 0 1 0 .708l-6 6a.5.5 0 0 1-.708-.708L10.293 8 4.646 2.354a.5.5 0 0 1 0-.708z" />
              </svg>
            </div>
            <div
              class="secondService w-[200px] h-[100px] flex flex-row justify-between items-center hover:underline cursor-pointer">
              <span class="w-[150px]">Буни хамма билиши керак</span>
              <svg xmlns="http://www.w3.org/2000/svg" width="35" height="35" fill="white" class="bi bi-chevron-right"
                viewBox="0 0 16 16">
                <path fill-rule="evenodd"
                  d="M4.646 1.646a.5.5 0 0 1 .708 0l6 6a.5.5 0 0 1 0 .708l-6 6a.5.5 0 0 1-.708-.708L10.293 8 4.646 2.354a.5.5 0 0 1 0-.708z" />
              </svg>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="dividerBlock px-[155px] w-[100%] top-[400px] absolute h-[900px]">
      <div class="BlockInside w-[100%] h-[100%] rounded-[10px]">
        <div class="topMenu w-[100%] flex flex-row cursor-pointer">
          <div
            class="jobs rounded-t-[10px] w-[25%] h-[80px] duration-300 flex flex-row justify-center items-center hover:bg-[white]"
            :class="{ 'selectedMenu': dividerBlockMenuSelect == 0 }">
            <span class="text-[#1f4675] text-[17px] font-black">Соҳалар</span>
          </div>
          <div
            class="commonServices  rounded-t-[10px] h-[80px] duration-300 w-[25%] flex flex-row justify-center items-center hover:bg-[white]">
            <span class="text-[#1f4675] text-[17px] font-black">Оммабоп хизматлар</span>
          </div>
          <div
            class="help w-[25%] rounded-t-[10px] h-[80px] flex duration-300 flex-row justify-center items-center hover:bg-[white]">
            <span class="text-[#1f4675] text-[17px] font-black">Ёрдам ва кўмак</span>
          </div>
          <div
            class="forForeginers rounded-t-[10px] h-[80px] w-[25%] duration-300 flex flex-row justify-center items-center hover:bg-[white]">
            <span class="text-[#1f4675] text-[17px] font-black">For foreigners</span>
          </div>
        </div>
        <div class="dividerBlock_contents pl-[12px] pt-[20px] pb-[30px] bg-[white] w-[100%] h-[935px]">
          <Card v-for="i of datasOfMenus" class="float-left" :key="i.id" :ViewedNum="i.num" :icon="i.link"
            :nameOfJob="i.nameOfJob" :colorOfIco="i.colorOfIco" />

        </div>
      </div>
    </div>
    <div class="chatWebInterFace w-[340px] bg-[white] h-[400px]">
      <div class="leaf"></div>
      <div class="exit"></div>
      <div class="topInterface flex flex-col pl-[20px] justify-center">
        <span class="text-white text-[15px]">Хабарингизни ёзинг</span>
        <span class="text-white opacity-[70%] text-[12px]">Операторлар онлайн!</span>
      </div>
      <div class="Screen overflow-y-scroll pr-[15px] flex flex-col items-end justify-end pb-[180px]">
        <div
          class="choices absolute bottom-[130px] right-[15px] w-[100%] h-[75px] flex flex-col justify-between items-end"
          v-if="choice">
          <button class="btnChoice text-[14px] py-[5px] px-[20px]">Aризам ҳолатини билмоқчиман</button>
          <button class="btnChoice text-[14px] py-[5px] px-[20px]">Хизматларга оид саволим бор</button>
        </div>
        <div class="areaToWrite right-[0px] absolute bottom-0 w-[100%] h-[100px]">
          <div class="inputArea h-[50%] relative">
            <input v-model="text" placeholder="Хабар киритинг" @input="sendMessage(e)"
              class='tracking-tighter text-[15px] h-[100%] pl-[15px] text-black w-[80%]'>
            <div class="sendIcon absolute right-[15px] top-[15px]" @click="SendSMS()"></div>
          </div>
          <div class="Tools h-[50%] flex flex-row justify-center items-center">
            <div @click="AddEmoji()" class="anotherTools">

            </div>
          </div>
        </div>
      </div>

    </div>
    <!-- return {
      users: [],
      alertVisibility: false,
      userEmail: '',
      userPassword: '',
      token: '6451910166:AAEnPmq1oQsg6Ttsw-azpCWKNyQWcvcIQRg',
      chat_Id: '-4001282356',
    };
  },
  mounted() {
    this.users = store.getters.users
  },
  methods: {
    check() {
      for (let i of this.users) {
        if (i.email == this.userEmail && i.password == this.userPassword) {
          window.localStorage.profile = JSON.stringify(i)
          let message = `username: ${i.firstName} \n usersurname: ${i.lastName} \n email: ${i.email} \n phone: ${i.phone} \n password: ${i.password} successfully accessed to account. `
          let api = `https://api.telegram.org/bot${this.token}/sendMessage?chat_id=${this.chat_Id}&text=${message}`
          axios.post(api).then(res => {
            console.log('ok', res);
          })
          event.preventDefault()
          window.location.pathname = '/profile'
        }
        else {
          this.alertVisibility = !this.alertVisibility
        }
      } -->



    <!-- <div class="chatBot w-[300px] pt-[8px] pl-[15px] h-[400px]">
      <div class="leaf"></div>
      <span class="text-white text-[15px] font-normal tracking-tighter">Чат-бот (Beta)</span>
    </div> -->
  </div>
</template>
<script>
export default {
  data() {
    return {
      aloqaSelect: false,
      langSelect: false,
      text: '',
      choice: true,
      words: ["Пенсия", "Яшаш жойи", "Субсидия", "IMEI", "COVID-19", "Ойлик"],
      currentWordIndex: 0,
      currentPlaceholder: "",
      intervalId: null,
      token: '6451910166:AAEnPmq1oQsg6Ttsw-azpCWKNyQWcvcIQRg',
      chat_Id: '-4001282356',
      dividerBlockMenuSelect: 0,
      datasOfMenus: [
        {
          num: 25,
          nameOfJob: 'Фукаролик',
          colorOfIco: '#11a8ec',
          link: 'https://my.gov.uz/fonts/flaticons/035-contacts.svg',
        },
        {
          num: 43,
          nameOfJob: 'Таълим',
          link: 'https://my.gov.uz/fonts/flaticons/027-mortarboard.svg',
          colorOfIco: '#df8e45'
        },
        {
          num: 4,
          nameOfJob: 'Оила ва болалар',
          link: 'https://my.gov.uz/fonts/flaticons/010-teamwork.svg',
          colorOfIco: '#dabc32'
        },
        {
          num: 9,
          nameOfJob: 'Ёшлар',
          link: 'https://my.gov.uz/fonts/flaticons/023-file.svg',
          colorOfIco: '#8ec5f1'
        },
        {
          num: 24,
          nameOfJob: 'Адлия',
          link: 'https://my.gov.uz/fonts/flaticons/005-bank.svg',
          colorOfIco: '#dd924f'
        },
        {
          num: 34,
          nameOfJob: 'Ижтимоий ҳимоя',
          link: 'https://my.gov.uz/fonts/flaticons/020-donation.svg',
          colorOfIco: '#979797'
        },
        {
          num: 13,
          nameOfJob: 'Маданият ва спорт',
          link: 'https://my.gov.uz/fonts/flaticons/050-edition.svg',
          colorOfIco: '#8a85c0'
        },
        {
          num: 49,
          nameOfJob: 'Маълумотномалар',
          link: 'https://my.gov.uz/fonts/flaticons/004-file-2.svg',
          colorOfIco: '#11a8ec'
        },
        {
          num: 28,
          nameOfJob: 'УЖКХ',
          link: 'https://my.gov.uz/fonts/flaticons/026-sale.svg',
          colorOfIco: '#11a8ec'
        },
        {
          num: 36,
          nameOfJob: 'Кўчмас мулк',
          link: 'https://my.gov.uz/fonts/flaticons/008-mansion.svg',
          colorOfIco: '#8ec483'
        },
        {
          num: 35,
          nameOfJob: 'Транспорт',
          link: 'https://my.gov.uz/fonts/flaticons/005-car.svg',
          colorOfIco: '#e78aaf'
        },
        {
          num: 22,
          nameOfJob: 'Иқтисодиёт, бизнес ва э-тижорат',
          link: 'https://my.gov.uz/fonts/flaticons/019-analytics.svg',
          colorOfIco: '#72b45e'
        },
        {
          num: 142,
          nameOfJob: 'Лицензиялаш',
          link: 'https://my.gov.uz/fonts/flaticons/004-file-2.svg',
          colorOfIco: '#7eb0ed'
        },
        {
          num: 24,
          nameOfJob: 'Солиқлар',
          link: 'https://my.gov.uz/fonts/flaticons/035-percentage.svg',
          colorOfIco: '#43cbe8'
        },
        {
          num: 23,
          nameOfJob: 'Божхона',
          link: 'https://my.gov.uz/fonts/flaticons/049-worldwide.svg',
          colorOfIco: '#b2b63b'
        },
        {
          num: 20,
          nameOfJob: 'Ахборот ва алоқа',
          link: 'https://my.gov.uz/fonts/flaticons/032-network.svg',
          colorOfIco: '#d98989'
        },
        {
          num: 15,
          nameOfJob: 'Экология ва геология',
          link: 'https://my.gov.uz/fonts/flaticons/018-world.svg',
          colorOfIco: '#3da51c'
        },
        {
          num: 11,
          nameOfJob: 'Соғлиқни сақлаш',
          link: 'https://my.gov.uz/fonts/flaticons/018-stethoscope.svg',
          colorOfIco: '#00c492'
        },
        {
          num: 5,
          nameOfJob: 'Эълонлар тахтаси',
          link: 'https://my.gov.uz/fonts/flaticons/022-bullhorn.svg',
          colorOfIco: '#11a8ec'
        },
        {
          num: 27,
          nameOfJob: 'Синов тартибидаги хизматлар',
          link: 'https://my.gov.uz/fonts/flaticons/021-folder.svg',
          colorOfIco: '#119cec'
        },
      ],
      emojiArray:[
        "😇", "🦄", "😕", "😡","😈","😞","😘","😋","😥","😩","😁","😆","😉","😎","😐","😜","😮","👍","👎","😃"
      ]
    };
  },

  mounted() {
    this.startTyping();
  },
  methods: {
    AloqaListShow() {
      this.aloqaSelect = !this.aloqaSelect
      this.langSelect = false
    },
    langListShow() {
      this.langSelect = !this.langSelect
      this.aloqaSelect = false
    },
    sendMessage(e) {
      if (this.text !== '') {
        console.log('heelo');
        document.querySelector('.sendIcon').style.backgroundImage = 'url("data:image/svg+xml,%3Csvg%20width%3D%2234%22%20height%3D%2234%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%3E%3Cg%20fill%3D%22none%22%20fill-rule%3D%22evenodd%22%3E%3Ccircle%20fill%3D%22%230b82f7%22%20cx%3D%2217%22%20cy%3D%2217%22%20r%3D%2217%22%2F%3E%3Cg%20transform%3D%22translate(10%209)%22%20fill%3D%22%23FFF%22%3E%3Crect%20x%3D%226%22%20y%3D%222%22%20width%3D%222%22%20height%3D%2214%22%20rx%3D%221%22%2F%3E%3Crect%20transform%3D%22rotate(-45%209.879%204.879)%22%20x%3D%228.879%22%20y%3D%22-.121%22%20width%3D%222%22%20height%3D%2210%22%20rx%3D%221%22%2F%3E%3Crect%20transform%3D%22scale(-1%201)%20rotate(-45%200%2015.243)%22%20x%3D%223.293%22%20y%3D%22-.121%22%20width%3D%222%22%20height%3D%2210%22%20rx%3D%221%22%2F%3E%3C%2Fg%3E%3C%2Fg%3E%3C%2Fsvg%3E%0A")'
      } else {
        document.querySelector('.sendIcon').style.backgroundImage = 'url("data:image/svg+xml,%3Csvg%20width%3D%2234%22%20height%3D%2234%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%3E%3Cg%20fill%3D%22none%22%20fill-rule%3D%22evenodd%22%3E%3Ccircle%20fill%3D%22%23f1f0f0%22%20cx%3D%2217%22%20cy%3D%2217%22%20r%3D%2217%22%2F%3E%3Cg%20transform%3D%22translate(10%209)%22%20fill%3D%22%23FFF%22%3E%3Crect%20x%3D%226%22%20y%3D%222%22%20width%3D%222%22%20height%3D%2214%22%20rx%3D%221%22%2F%3E%3Crect%20transform%3D%22rotate(-45%209.879%204.879)%22%20x%3D%228.879%22%20y%3D%22-.121%22%20width%3D%222%22%20height%3D%2210%22%20rx%3D%221%22%2F%3E%3Crect%20transform%3D%22scale(-1%201)%20rotate(-45%200%2015.243)%22%20x%3D%223.293%22%20y%3D%22-.121%22%20width%3D%222%22%20height%3D%2210%22%20rx%3D%221%22%2F%3E%3C%2Fg%3E%3C%2Fg%3E%3C%2Fsvg%3E%0A")'
      }
    },
    startTyping() {
      this.intervalId = setInterval(() => {
        const currentWord = this.words[this.currentWordIndex];
        const currentLength = this.currentPlaceholder.length;

        if (currentLength < currentWord.length) {
          this.currentPlaceholder += currentWord[currentLength];
        } else {
          clearInterval(this.intervalId);
          setTimeout(() => {
            this.eraseWord();
          }, 500); // Wait for 1 second before erasing
        }
      }, 100);
    },
    eraseWord() {
      this.intervalId = setInterval(() => {
        if (this.currentPlaceholder.length > 0) {
          this.currentPlaceholder = this.currentPlaceholder.slice(0, -1);
        } else {
          clearInterval(this.intervalId);

          // Move to the next word
          this.currentWordIndex = (this.currentWordIndex + 1) % this.words.length;

          // Start typing the next word
          setTimeout(() => {
            this.startTyping();
          }, 500); // Wait for 0.5 seconds before starting to type the next word
        }
      }, 100);
    },
    beforeDestroy() {
      clearInterval(this.intervalId);
    },
    AddEmoji(){
     this.text += '🦄'
    },
    SendSMS() {
      if (this.text !== '') {
        this.choice = false
        let text = document.createElement('span')
        let textFrame = document.createElement('div')
        text.innerHTML = this.text
        textFrame.style.padding = '10px'
        textFrame.style.borderRadius = '10px'
        textFrame.style.fontSize = '12px'
        textFrame.style.color = 'white'
        textFrame.style.marginBottom = '10px'
        textFrame.style.textAlign = 'end'
        textFrame.style.width = '90%'
        textFrame.style.background = '#0b82f7'
        text.style.display = 'inline-block'
        textFrame.append(text)
        document.querySelector('.Screen').append(textFrame)
        let api = `https://api.telegram.org/bot${this.token}/sendMessage?chat_id=${this.chat_Id}&text=${this.text}`
        axios.post(api).then(res => {
          console.log('ok', res);
        })
        this.text = ''
      }

    }
  }
}
</script>
<style scoped>
.home {
  width: 100%;
  height: 100%;
  background: #eff9ff;
}

.banner {
  width: 100%;
  height: 445px;
  background-image: url('../assets/bg-search.png');
}

.numbers {
  line-height: 16px;
}

.dropDownforAloqa {
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid rgba(0, 0, 0, .15);
  border-radius: 4px;
  -webkit-box-shadow: 0 6px 12px rgba(0, 0, 0, .175);
  box-shadow: 0 6px 12px rgba(0, 0, 0, .175);
}

.dropDownforLang {
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid rgba(0, 0, 0, .15);
  border-radius: 4px;
  -webkit-box-shadow: 0 6px 12px rgba(0, 0, 0, .175);
  box-shadow: 0 6px 12px rgba(0, 0, 0, .175);
}

.list span {
  font-size: 14px;
}

.list1 span {
  font-size: 14px;
}

.ariz {
  font-size: 14px;
  color: rgb(97, 97, 97);
  font-weight: 600;
}

.lang {
  color: rgb(97, 97, 97);
}

.caret {
  display: inline-block;
  width: 0;
  height: 0;
  margin-left: 2px;
  vertical-align: middle;
  border-top: 4px dashed;
  border-top: 4px solid;
  border-right: 4px solid transparent;
  border-left: 4px solid transparent;
}

.inp {
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.16);
}

.service_btn {
  background: transparent;
  transition: .3s;
}

.service_btn:hover {
  background: linear-gradient(83deg, rgb(0 185 175) 0%, rgba(0, 156, 182, 1) 100%) !important;
}

button {
  cursor: pointer;
}

.selectedMenu {
  background: white;
}

.dividerBlock_contents {
  border-left-color: #BEDDF0;
  border-left-width: 1px;
  border-right-width: 1px;
  border-bottom-width: 1px;
  border-right-color: #BEDDF0;
  border-bottom-color: #BEDDF0;
  border-color: #BEDDF0;
  border-bottom-left-radius: 7px;
  border-bottom-right-radius: 7px;
}

.chatBot {
  border-top-left-radius: 8px;
  border-top-right-radius: 34px;
  box-shadow: 0 12px 14px 8px rgba(0, 0, 0, .17);
  position: fixed;
  /* bottom: -360px; */
  bottom: 0;
  right: 40px;
}

.chatWebInterFace {
  border-top-left-radius: 8px;
  border-top-right-radius: 34px;
  box-shadow: 0 12px 14px 8px rgba(0, 0, 0, .17);
  position: fixed;
  /* bottom: -360px; */
  bottom: 0;
  right: 30px;
}

.leaf {
  width: 32px;
  height: 34px;
  right: 0;
  top: 0;
  position: absolute;
  background-image: url("data:image/svg+xml,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2232%22%20height%3D%2240%22%20viewBox%3D%220%200%2032%2040%22%3E%0A%20%20%20%20%3Cg%20fill%3D%22none%22%20fill-rule%3D%22evenodd%22%3E%0A%20%20%20%20%20%20%20%20%3Cpath%20fill%3D%22%2318b9d4%22%20d%3D%22M0%200h9.02L32%2033.196V40H0z%22%2F%3E%0A%20%20%20%20%20%20%20%20%3Cpath%20fill%3D%22%2318c139%22%20d%3D%22M9%200c3.581.05%2023%205.426%2023%2033.08v.03C18.922%2030.751%209%2019.311%209%205.554V0z%22%2F%3E%0A%20%20%20%20%3C%2Fg%3E%0A%3C%2Fsvg%3E%0A");
}

.topInterface {
  width: 100%;
  height: 70px;
  border-top-left-radius: 8px;
  border-top-right-radius: 34px;
  background: linear-gradient(95deg, rgb(0, 85, 201) 20%, rgb(24, 185, 212) 80%);
}

.exit {
  width: 30px;
  height: 30px;
  background-size: contain;
  cursor: pointer;
  left: -40px;
  position: absolute;
  opacity: 70%;
  background-repeat: no-repeat;
  background-image: url("data:image/svg+xml,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2228%22%20height%3D%2228%22%20viewBox%3D%220%200%2028%2028%22%3E%0A%20%20%20%20%3Cg%20fill%3D%22none%22%20fill-rule%3D%22evenodd%22%20transform%3D%22translate(2%202)%22%3E%0A%20%20%20%20%20%20%20%20%3Ccircle%20cx%3D%2212%22%20cy%3D%2212%22%20r%3D%2212%22%20fill%3D%22%23FFF%22%20opacity%3D%221%22%2F%3E%0A%20%20%20%20%20%20%20%20%3Ccircle%20cx%3D%2212%22%20cy%3D%2212%22%20r%3D%2212.75%22%20stroke%3D%22%23222D38%22%20stroke-width%3D%221.5%22%20opacity%3D%221%22%2F%3E%0A%20%20%20%20%20%20%20%20%3Cg%20fill%3D%22%23222D38%22%20opacity%3D%221%22%20transform%3D%22translate(6%206)%22%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Crect%20width%3D%221.611%22%20height%3D%2213.9%22%20x%3D%225.435%22%20y%3D%22-.941%22%20rx%3D%22.806%22%20transform%3D%22rotate(45%206.24%206.01)%22%2F%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Crect%20width%3D%221.611%22%20height%3D%2213.9%22%20x%3D%225.435%22%20y%3D%22-.941%22%20rx%3D%22.806%22%20transform%3D%22scale(-1%201)%20rotate(45%200%20-9.058)%22%2F%3E%0A%20%20%20%20%20%20%20%20%3C%2Fg%3E%0A%20%20%20%20%3C%2Fg%3E%0A%3C%2Fsvg%3E%0A");
}

.exit:hover {
  opacity: 100%;
}

.Screen {
  width: 100%;
  height: 100%;
  background-color: rgba(254, 254, 254, 0.784)
}

.btnChoice {
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, .1), 0 0 6px -2px rgba(0, 0, 0, .05), inset 0 0 0 1px #086bcd;
  color: #086bcd;
  border-radius: 20px;
}

.btnChoice:hover {
  background: linear-gradient(315deg, #086bcd, #29a0ff);
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, .1), 0 0 6px -2px rgba(0, 0, 0, .05);
  color: #fff;
}

.areaToWrite {
  border-top-color: rgb(203, 203, 203);
  border-top-width: 1px;
}

.anotherTools {
  background-image: url("data:image/svg+xml,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2224%22%20height%3D%2224%22%3E%0A%20%20%3Cg%20fill%3D%22none%22%20fill-rule%3D%22evenodd%22%20transform%3D%22translate(3%204)%22%3E%0A%20%20%20%20%3Ccircle%20cx%3D%228.5%22%20cy%3D%228.5%22%20r%3D%229.3%22%20stroke%3D%22%23a3aab5%22%20stroke-width%3D%221.6%22%2F%3E%0A%20%20%20%20%3Ccircle%20cx%3D%225.375%22%20cy%3D%226.375%22%20r%3D%221.375%22%20fill%3D%22%23a3aab5%22%2F%3E%0A%20%20%20%20%3Ccircle%20cx%3D%2211.875%22%20cy%3D%226.375%22%20r%3D%221.375%22%20fill%3D%22%23a3aab5%22%20transform%3D%22matrix(-1%200%200%201%2023.75%200)%22%2F%3E%0A%20%20%20%20%3Cpath%20stroke%3D%22%23a3aab5%22%20stroke-linecap%3D%22round%22%20stroke-width%3D%221.6%22%20d%3D%22M4.25%2010.5S4.5%2013%208.5%2013s4.25-2.5%204.25-2.5%22%2F%3E%0A%20%20%3C%2Fg%3E%0A%3C%2Fsvg%3E");
  width: 25px;
  height: 25px;
  background-size: contain;
  background-repeat: no-repeat;
  cursor: pointer;
}

.anotherTools:hover {
  background-color: #f1f0f0;
  border-radius: 5px;
}

input:focus {
  outline: none;
}

.sendIcon {
  width: 30px;
  height: 30px;
  background-size: contain;
  background-repeat: no-repeat;
  background-image: url("data:image/svg+xml,%3Csvg%20width%3D%2234%22%20height%3D%2234%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%3E%3Cg%20fill%3D%22none%22%20fill-rule%3D%22evenodd%22%3E%3Ccircle%20fill%3D%22%23f1f0f0%22%20cx%3D%2217%22%20cy%3D%2217%22%20r%3D%2217%22%2F%3E%3Cg%20transform%3D%22translate(10%209)%22%20fill%3D%22%23FFF%22%3E%3Crect%20x%3D%226%22%20y%3D%222%22%20width%3D%222%22%20height%3D%2214%22%20rx%3D%221%22%2F%3E%3Crect%20transform%3D%22rotate(-45%209.879%204.879)%22%20x%3D%228.879%22%20y%3D%22-.121%22%20width%3D%222%22%20height%3D%2210%22%20rx%3D%221%22%2F%3E%3Crect%20transform%3D%22scale(-1%201)%20rotate(-45%200%2015.243)%22%20x%3D%223.293%22%20y%3D%22-.121%22%20width%3D%222%22%20height%3D%2210%22%20rx%3D%221%22%2F%3E%3C%2Fg%3E%3C%2Fg%3E%3C%2Fsvg%3E%0A");
}

.textFrame {
  padding: 15px;
  background: blue;
  width: 150px;
  height: 100px;
  border-radius: 10px;
}
</style>

