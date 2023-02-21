<script setup>
import { computed, ref, watchEffect } from 'vue'
const perspective = ref(1500)
const perspectiveOpen = () => {
  if (perspective.value === 0) {
    perspective.value = 150
  } else {
    perspective.value = 0
  }
}
const num = ref(10)
const style = ref({})
const threeD = ref(false)
const rotateY = ref(0)
const rotateX = ref(30)
const rotateZ = ref(0)
const translateZ = ref(0)
const styleVar = computed(() => {
  return `rotateY(${rotateY.value}deg)` + `rotateZ(${rotateZ.value}deg)` + `translateZ(${translateZ.value}px)`
})
const div2Style = computed(() => {
  return `rotateX(${rotateX.value}deg)`
})
watchEffect(() => {
  if (rotateX.value === 180) {
    num.value++
  }
})
</script>

<template>
  <div class="perspective">
    <div class="input">
      <div class="btns">
        <button type="primary" @click="threeD = !threeD">{{ !threeD ? "开启3D" : "关闭3D" }}</button>
      </div>
      <div>视距调整(perspective): {{ perspective === 0 ? 'none': perspective + 'px' }}</div>
      <input class="r" type="range" min="0" max="1000" step="10" v-model="perspective" />
      <div>左旋转角度(rotateY): {{ rotateY }}deg</div>
      <input class="r" type="range" min="0" max="360" step="1" v-model="rotateY" />
      <div>上旋转角度(rotateX): {{ rotateX }}deg</div>
      <input class="r" type="range" min="0" max="360" step="1" v-model="rotateX" />
      <div>上旋转角度(rotateZ): {{ rotateZ }}deg</div>
      <input class="r" type="range" min="0" max="360" step="1" v-model="rotateZ" />
      <div>上旋转角度(translateZ): {{ translateZ }}px</div>
      <input class="r" type="range" min="0" max="360" step="1" v-model="translateZ" />
    </div>
    <div
      :class="['container', threeD ? 'threeD' : '']"
      :style="{
				'--perspective': perspective > 0 ? perspective + 'px' : 'none',
				transform: styleVar,
			}"
    >
      <div class="div1" :class="[threeD ? 'threeD' : '']">
        <div class="div2" :style="{transform: div2Style}"></div>
      </div>
    </div>
  </div>
</template>
<style scoped>
.perspective {
  width: 100%;
  height: 500px;
  display: flex;
}
.btns {
  display: flex;
}
button {
  padding: 0.3em;
  background-color: #000;
  outline: none;
  color: #fff;
  font-size: 12px;
  border-radius: 3px;
}
.container {
  display: flex;
  justify-content: center;
  justify-content: center;
  position: inherit;
}
.input {
  box-sizing: border-box;
  width: 200px;
}
.input button {
  margin: 0.5em 0.2em;
}
.input div {
    font-size: 12px;
}
.threeD {
  transform-style: preserve-3d;
}

.div1 {
  position: relative;
  height: 150px;
  width: 150px;
  margin: 50px;
  padding: 10px;
  border: 1px solid black;
  background-image: linear-gradient(135deg, #17ead9, #6078ea);
  box-sizing: content-box;
  perspective: var(--perspective);
  -webkit-perspective: var(--perspective);
}

.div2 {
  height: 150px;
  width: 150px;
  line-height: 150px;
  font-size: 100px;
  color: #fff;
  text-align: center;
  position: absolute;
  border: 1px solid black;
  background: #faf;
  transform: rotateX(30deg);
  -webkit-transform: rotateX(30deg);
}
</style>
