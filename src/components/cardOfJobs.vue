<template>
    <div class="card relative flex justify-center w-[200px] rounded-[8px] h-[200px] border-[1px] border-[black]">
        <div class="topIcon">
            <span>{{ ViewedNum }}</span>
        </div>
        <div class="centerIcon flex flex-row justify-center items-center">
            <img class="ico w-[35px]" :src="icon" alt="">
        </div>
        <span class="absolute bottom-[45px] text-[15px] font-black tracking-wide">{{ nameOfJob }}</span>
    </div>
</template>

<script>
export default {
    name: '',

    data() {
        return {

        };
    },

    mounted() {

    },
    props: {
        ViewedNum: Number,
        nameOfJob: String,
        backgroundColor: String,
        icon: String,

    },

    methods: {

    },
};
</script>

<style scoped>
.topIcon {
    border-radius: 15px 2px 15px 2px;
    width: 38px;
    height: 30px;
    text-align: center;
    padding-top: 4px;
    position: absolute;
    right: 15px;
    top: 15px;
    font-size: 13px;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: baseline;
    background: #7fd963;
    color: white !important;
}

.centerIcon {
    width: 62px;
    height: 62px;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translateX(-50%) translateY(-70%);
    background: blue;
    border-radius: 16px;
    text-align: center;
}
.ico{
    filter: brightness(0) invert(1);
}
</style>