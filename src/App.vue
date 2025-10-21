<template>
  <div class="main">
    <div class="name" v-if="!isEnter"><img src="./assets/name.webp" alt=""></div>
    <div class="titleBox">
      <div v-if="!isEnter" class="innerTitle">IT STUDIO</div>
    </div>
    <div class="enter hover-animation-blue" @click="scrollDown" v-if="!isEnter">ENTER</div>
    <div class="text" v-if="!isEnter">
      <span>中国海洋大学 | 西海岸58创新创业工坊 | @ITStudio All Rights Reserved |</span>
      <a href="https://beian.miit.gov.cn/" target="_blank">备案号:桂ICP备2022004639号-2</a>
    </div>
    <div ref="backgd" class="covers">
      <div class="cover">
        <div class="waves" v-if="isEnter">
          <img src="./assets/wave-1.svg" />
          <img src="./assets/wave-2.svg" />
          <img src="./assets/wave-3.svg" />
          <img src="./assets/wave-4.svg" />
          <img src="./assets/wave-5.svg" id="shape" />
        </div>
        <div class="blue">
          <img src="./assets/flowBtm.webp" alt="" ref="flowB">
          <img src="./assets/flowCtr.webp" alt="" ref="flowC">
          <img src="./assets/flowTop.webp" alt="" ref="flowT">
        </div>
      </div>
    </div>
    <div ref="mainer" class="mainer">
      <h2>爱特工作室</h2>
      <div class="lists" ref="lists">
        <div class="year y2023 p5-hover-animation-mix" @mouseover="open23" @mouseleave="leave">
          <a href="https://2023.itstudio.club" target="_blank">2024级</a>
        </div>
        <div class="year y2022 p5-hover-animation-mix" @mouseover="open22" @mouseleave="leave">
          <a href="https://2022.itstudio.club" target="_blank">2023级</a>
        </div>
        <div class="year y2021 p5-hover-animation-mix" @mouseover="open21" @mouseleave="leave">
          <a href="https://2021.itstudio.club" target="_blank">2022级</a>
        </div>
        <div class="title">点击查看历年迎新网</div>
      </div>
      <div class="listbg"><img src="./assets/listbg.webp" alt=""></div>
      <div class="show">
        <div class="start" :class="{ 'showUP': !hover }">
          爱特工作室成立于2002年,是一个在中国海洋大学信息科学与工程学部领导主持下,以计算机技术人才培养,网络开发为特色的技术性团体。</div>
        <div class="show23" :class="{ 'showUP': hover23 }"><img src="./assets/2023.webp" alt=""></div>
        <div class="show22" :class="{ 'showUP': hover22 }"><img src="./assets/2022.webp" alt=""></div>
        <div class="show21" :class="{ 'showUP': hover21 }"><img src="./assets/2021.webp" alt=""></div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const backgd = ref(null);
const flowB = ref(null);
const flowC = ref(null);
const flowT = ref(null);
const mainer = ref(null)
const lists = ref(null)

const isEnter = ref(false);

const hover = ref(false);
const hover23 = ref(false);
const hover22 = ref(false);
const hover21 = ref(false);

function scrollDown() {
  const newTop = 98;
  backgd.value.style.backgroundColor = "rgb(70, 155, 229,1)"
  backgd.value.style.top = `${newTop}vh`;
  flowB.value.style.height = `104%`;
  flowC.value.style.height = `104%`;
  flowT.value.style.height = `104%`;
  isEnter.value = true;
  mainer.value.style.top = '0'
  lists.value.style.right = '8vh'
}

function open23() {
  hover23.value = true;
  hover.value = true;
}

function open22() {
  hover22.value = true;
  hover.value = true;
}

function open21() {
  hover21.value = true;
  hover.value = true;
}

function leave() {
  hover23.value = false;
  hover22.value = false;
  hover21.value = false;
  hover.value = false;
}
</script>


<style scoped>
* {
  padding: 0;
  margin: 0;
}

a {
  color: black;
  text-decoration: none !important;
}

body {
  padding: 0;
  margin: 0;
}

.main {
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  overflow: hidden;
  min-width: 1300px;
  background-image: url(./assets/bg.webp);
  background-repeat: no-repeat;
  background-position-x: center;
  background-position-y: center;
  background-size: cover;
  background-attachment: fixed;
}

.name {
  width: 120vh;
  z-index: 2;
}


.name img {
  width: 100%;
}

.text {
  position: absolute;
  bottom: 10px;
  margin-bottom: 10px;
  color: #FFF;
  font-family: Poppins;
  font-size: 16px;
  font-style: normal;
  font-weight: 500;
  line-height: normal;
  letter-spacing: 2.08px;
  z-index: 100;
}

.text a {
  color: #FFF;
  font-family: Poppins;
  font-size: 16px;
  font-style: normal;
  font-weight: 500;
  line-height: normal;
  letter-spacing: 2.08px;
}



.titleBox .innerTitle {
  letter-spacing: 0.5vw;
  /* width: 35vw; */
  font-size: 6.67vw;
  font-family: monospace;
  font-weight: bolder;
  color: #FFF;
  margin-bottom: 1.5vw;
  position: relative;
  text-align: left;
  /* 打字动画实现  */
  white-space: nowrap;
  overflow: hidden;
  animation: typing 2s steps(9) forwards;
  z-index: 2;
}

.titleBox .innerTitle::after {
  content: "";
  position: absolute;
  top: 0;
  right: 0;
  width: 0.4vw;
  height: 100%;
  background: #fff;
  animation: blink 1s linear infinite;
  animation-delay: 2.5s;
}

/* 动画 */
/* 1. 打字效果的光标闪烁 */
@keyframes blink {

  0%,
  49% {
    opacity: 1;
  }

  50%,
  100% {
    opacity: 0;
  }
}

/* 2. 打字动画 */
@keyframes typing {
  0% {
    width: 0;
  }

  100% {
    width: 36vw;
  }

  /* 100% {
    width: 0;
  } */
}

.enter {
  transition: 0.2s;
  font-size: 60px;
  color: #FFF;

  z-index: 2;
}

.enter:hover {
  cursor: pointer;
  transition: 0.2s;
  transform: translateY(-1vh) rotate(-4deg) scale(1.15);
}

.hover-animation-blue {
  position: relative;
  z-index: 2;
}

.hover-animation-blue:before {
  content: "";
  position: absolute;
  width: 100%;
  height: 100%;
  z-index: -1
}

.hover-animation-blue:hover:before {
  background: #1cfeff;
  animation: bg 1s ease-out infinite
}

@keyframes bg {
  0% {
    top: 6%;
    transform: skew(-10deg, -2deg) scale(.9)
  }

  20% {
    top: 3%;
    transform: skew(35deg, 4deg) scale(.9)
  }

  40% {
    top: -2%;
    transform: skew(-20deg, -2deg) scale(.95)
  }

  60% {
    top: -4%;
    transform: skew(20deg, 2deg) scale(1)
  }

  80% {
    top: 3%;
    transform: skew(-25deg, -4deg) scale(.94)
  }

  to {
    top: 6%;
    transform: skew(-10deg, -2deg) scale(.9)
  }
}

.waves {
  display: block;
  width: 100%;
  height: 100%;
}

#shape {
  position: absolute;
  left: 0;
  bottom: -30px;
  height: 80%;
}

/* .waves img:not(#shape) {
  position: absolute;
  left: 0;
  top: 0;
} */

.waves img:nth-child(1) {
  opacity: 0.8;
  top: 0;
  animation: move-1 5s infinite;
}

@keyframes move-1 {
  50% {
    transform: translateY(-20px);
  }
}

.waves img:nth-child(2) {
  opacity: 0.7;
  top: 0;
  animation: move-2 3s infinite;
}

@keyframes move-2 {
  50% {
    transform: translateY(-20px);
  }
}

.waves img:nth-child(3) {
  top: 0;
  opacity: 0.6;
  animation: move-3 3.5s infinite;
}

@keyframes move-3 {
  50% {
    transform: translateY(-20px);
  }
}

.waves img:nth-child(4) {
  top: 0;
  opacity: 0.5;
  animation: move-4 3s infinite;
}

@keyframes move-4 {
  50% {
    transform: translateY(-20px);
  }
}

.covers {
  position: absolute;
  top: 0;
  height: 100vh;
  width: 100%;
  z-index: 1;
  transition: 1.4s;
}

.cover {
  height: 100vh;
  position: relative;
}

.cover .waves {
  position: absolute;
  height: 160px;
  top: -160px;
  z-index: 100;
}

.cover .waves img {
  height: 200px;
  width: 100%;
  position: absolute;
  bottom: 0;
}

.cover .blue {
  width: 100%;
  height: 100vh;
  background-color: rgb(70, 155, 229, 0);
  position: relative;
  transition: 0;
  z-index: 2;
}

.blue img {
  position: absolute;
  /* height: 100%; */
  width: 200%;
  bottom: 0;
}

.blue img:nth-child(1) {
  z-index: 4;
  height: 40%;
  animation: moveFlow 7s linear infinite;
}

.blue img:nth-child(2) {
  z-index: 3;
  height: 70%;
  animation: moveFlow2 6s linear infinite;
}

.blue img:nth-child(3) {
  z-index: 2;
  height: 100%;
  animation: moveFlow 2s linear infinite;
}

@keyframes moveFlow {
  0% {
    left: -100%;
  }

  100% {
    left: 0;
  }
}

@keyframes moveFlow2 {
  0% {
    right: -100%;
  }

  100% {
    right: 0;
  }
}

.mainer {
  height: 100vh;
  width: 100vw;
  min-width: 1500px;
  position: absolute;
  top: 100vh;
  transition: 1.8s;
}

.mainer h2 {
  font-size: 14vh;
  height: 18vh;
  width: 70vh;
  color: #ffffff09;
  background-image: url(./assets/textbg.webp);
  background-size: 100% 100%;
  background-clip: text;
  position: absolute;
  left: 12vh;
  top: 6vh;
}

.mainer .lists .title {
  font-size: 20px;
}

.mainer .year {
  width: 120px;
  height: 60px;
  font-size: 30px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.year a {
  transition: 0.2s;
  color: black;
  font-weight: 700;
}

.year:hover {
  transition: 0.2s;
  transform: translateY(-6px) rotate(-5deg) scale(1.15);
}

.lists {
  position: absolute;
  top: 0;
  height: 100vh;
  width: 26vw;
  background-image: url(./assets/listbg.webp);
  background-size: 100% 100%;
  right: -50vh;
  z-index: 0;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: end;
  transition: 2s;
}

.y2023 {
  transform: translateX(-3vh);
}

.y2023:hover {
  transform: translateX(-3vh) translateY(-6px) rotate(-5deg) scale(1.15);
}

.y2022 {
  transform: translateX(-8vh);
}

.y2022:hover {
  transform: translateX(-8vh) translateY(-6px) rotate(-5deg) scale(1.15);
}

.y2021 {
  transform: translateX(-12vh);
}

.y2021:hover {
  transform: translateX(-12vh) translateY(-6px) rotate(-5deg) scale(1.15);
}


.title {
  transform: translateX(-12vh);
}

.listbg {
  position: absolute;
  top: 0;
  right: 12vh;
  height: 100vh;
  opacity: 0.8;
  z-index: 0;
  display: none;
}

.listbg img {
  height: 100%;
}

.mainer .show {
  position: absolute;
  left: 15vh;
  top: 28vh;
  background-color: rgba(245, 245, 245, 0.486);
  border-radius: 2vh;
  width: 110vh;
  height: 60vh;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}

.show .start {
  transition: 0.5s;
  font-size: 32px;
  width: 90vh;
  opacity: 0;
  position: absolute;
  top: 40%;
  /* transform: translateY(-50%); */
}

.show div {
  transition: 0.5s;
  width: 110vh;
  height: 60vh;
  position: absolute;
  top: 0;
  opacity: 0;
}

.show div img {
  height: 100%;
}

.showUP {
  transition: 0.5s;
  opacity: 1 !important;
}
</style>