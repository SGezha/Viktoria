<script setup>
import YAML from 'js-yaml'
import { computed, reactive, ref } from 'vue'
import { useMediaQuery, useParallax } from '@vueuse/core'

const target = ref(null)
const isMobile = useMediaQuery('(max-width: 700px)')

const parallax = reactive(useParallax(target))

const targetStyle = {
  // display: 'flex',
  // flexDirection: 'column',
  // justifyContent: 'center',
  minHeight: '500px',
  transition: '.3s ease-out all'
}
const cardWindowStyle = {
  overflow: 'hidden',
  position: 'absolute',
  top: '0px',
  left: '0px',
  height: '100%',
  width: '100%'
}
const layerBase = {
  position: 'absolute',
  height: '100%',
  width: '100%',
  transition: '.3s ease-out all'
}
const containerStyle = {
  // margin: '1em auto',
  // perspective: '500px',
  // display: 'flex'
}

const infoStyle = computed(() => ({
  opacity: 0.4,
  top: '20px',
  left: '40px',
  position: isMobile.value ? 'inherit' : 'absolute'
}))

const vika = computed(() => ({
  ...layerBase,
  transform: `translateX(${parallax.tilt * 50}px) translateY(${
    parallax.roll * 50
  }px) scale(1.33)`
}))

const bgLayer = computed(() => ({
  ...layerBase,
  transform: `translateX(${parallax.tilt * 100}px) translateY(${
    parallax.roll * 100
  }px) scale(1.33)`
}))

const kadzuha = computed(() => ({
  ...layerBase,
  transform: `translateX(${parallax.tilt * 100}px) translateY(${
    parallax.roll * 100
  }px) scale(1.33)`
}))

const flower_1 = computed(() => ({
  ...layerBase,
  transform: `translateX(${parallax.tilt * 50}px) translateY(${
    parallax.roll * 50
  }px) scale(1.33)`
}))

const text_block = computed(() => ({
  ...layerBase,
  transform: `translateX(${parallax.tilt * 500}px) translateY(${
    parallax.roll * 500
  }px) scale(1.33)`
}))

const bg_back = computed(() => ({
  ...layerBase,
  transform: `translateX(${parallax.tilt * 100}px) translateY(${
    parallax.roll * 100
  }px) scale(1.33)`
}))

const layer4 = layerBase

const cardStyle = computed(() => ({
  // height: '90svw',
  // width: '90svw',
  // borderRadius: '5px',
  // border: '1px solid #cdcdcd',
  // overflow: 'hidden',
  position: 'absolute',
  transition: '.3s ease-out all'
  // boxShadow: '0 0 20px 0 rgba(255, 255, 255, 0.5)',
  // transform: `rotateX(${parallax.roll * 0}deg) rotateY(${
  //   parallax.tilt * 0
  // }deg)`
}))
</script>

<template>
  <div>
    <div ref="target" :style="targetStyle">
      <!-- <pre :style="infoStyle">{{ YAML.dump(parallax) }}</pre> -->
      <div :style="containerStyle">
        <div class="card_style" :style="cardStyle">
          <div :style="cardWindowStyle">
            <img :style="vika" class="img_block vika" src="/art.png" alt="" />
            <img
              :style="bgLayer"
              class="img_block bg_block"
              src="/bg1.jpg"
              alt=""
            />
            <img
              :style="kadzuha"
              class="img_block kadzuha"
              src="/kadzhuha.png"
              alt=""
            />
            <img
              :style="flower_1"
              class="img_block flower_1"
              src="/flower_1.png"
              alt=""
            />
            <img
              :style="bg_back"
              class="img_block bg_back"
              src="/bg_back.png"
              alt=""
            />
            <div class="img_block text_block" :style="text_block">
              <div class="vika_text">
                Вика ❤️<br />
                с 8 Марта
              </div>
            </div>
            <!-- <img
              :style="layer4"
              class="img_block"
              src="https://jaromvogel.com/images/design/jumping_rabbit/page2layer4.png"
              alt=""
            /> -->
          </div>
        </div>
      </div>
      <div class="authors">
        <div class="opacity-1">Dev by SGezha with ❤️</div>
        <div class="opacity-1">
          Спасибо за арт
          <a href="https://vk.com/lavandosart" target="__blank">lavandosart</a>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Pacifico&display=swap');

* {
  font-family: 'Pacifico', cursive;
  font-weight: 400;
  font-style: normal;
}

.text_block {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 60px;
  z-index: 1;
  background-blend-mode: normal;
}

.vika_text {
  color: white;
}

.img_block {
  left: 0;
  top: 0;
}

.authors {
  position: fixed;
  bottom: 10px;
  left: 10px;
  text-align: left;
  opacity: 0.3;
  z-index: 10;
  font-size: 10px;
}

.card_style {
  width: 100vw;
  height: 100vh;
  width: 100dvw;
  height: 100dvh;
  position: fixed;
}

.card_style::after {
  content: '';
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  /* background: url(/bg.jpg); */
  background-position: 50% 50%;
  height: 100%;
  filter: blur(4px);
  z-index: -1;
}

.vika {
  z-index: 2;
  object-fit: contain;
}

.bg_block {
  position: absolute;
  height: 100% !important;
  width: 100%;
  object-fit: cover;
  filter: blur(5px);
  z-index: -1;
}

.flower_1 {
  z-index: 2;
  filter: blur(2px);
  height: 100% !important;
  width: 100%;
  object-fit: cover;
}

.bg_back {
  z-index: 3;
  filter: blur(2px);
  height: 100% !important;
  width: 100%;
  object-fit: cover;
}

.kadzuha {
  position: absolute;
  height: 100% !important;
  width: 100%;
  object-fit: cover;
  filter: blur(1px);
  z-index: 2;
}
</style>
