<script setup lang="ts">
import { computed, ref } from "vue";

const props = defineProps({
	zPx: {
		default: -1500,
	},
});
const threeD = ref(false)
const perspectiveOpen = ref(false);
const styleVar = computed(() => {
	return {
        'perspective': perspectiveOpen.value ? '1000px' : 'none',
		"--zPx": props.zPx + "px",
	};
});
</script>
<template>
	<div :class="['demo', threeD ? 'threeD' : '']">
        <div class="operation">
            <button @click="threeD = !threeD">{{threeD ? "关闭" : '开启'}}3D</button>
            <button @click="perspectiveOpen = !perspectiveOpen">{{perspectiveOpen ? "关闭" : '开启'}}perspective</button>
        </div>
		<div
			:class="['test_container', threeD ? 'threeD' : '']"
			:style="styleVar"
		>
			<div class="box"></div>
		</div>
	</div>
</template>
<style scoped>
.demo {
	perspective: 1000px;
	transform-origin: center center;
	transform-style: preserve-3d;
}
.test_container {
	position: relative;
	width: 200px;
	height: 200px;
	border: 1px solid #666;
    background-image: linear-gradient(135deg, #17ead8aa, #001682ba);
    /* backdrop-filter: contrast(0.6); */
    /* opacity: 0.7; */
	box-sizing: content-box;
	padding: 20px;
	transform: rotateY(-30deg);
}
.threeD {
	transform-origin: center center;
	transform-style: preserve-3d;
}
.operation {
    border-bottom: 1px dashed rgb(16, 12, 12);
    padding: 0.5em 1em;
    margin-bottom: 1em;
}
.operation button {
    padding: 0.3em 1em;
    background-color:#000;
    outline: none;
    color: #fff;
    font-size: 18px;
    border-radius: 5px;
    margin-right: 0.5em;
}
.box {
	width: 200px;
	height: 200px;
	background-image: url("/imgs/GREEN.png");
	background-size: 100% 100%;
	transform: translateZ(var(--zPx)) rotateX(45deg);
	z-index: 1;
}
</style>
