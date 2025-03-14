<template>
	<div>
		<h1>Home</h1>
		<div class="box" ref="box">box</div>
	</div>
</template>

<script setup>
import { onBeforeRouteLeave } from 'vue-router';
import {onMounted} from 'vue';
import gsap from 'gsap';
import { ref } from 'vue';

const box = ref(null)

onMounted(() => {
	console.log(box.value);

	gsap.from(box.value,
	{ rotation: 27,
		x: 100,
		duration: 1,
		onComplete: () => {
		}
	});
}),

onBeforeRouteLeave((to, from, next) => {
	console.log('frerot je pars');

	gsap.to(box.value,
	{ rotation: 27,
		y: 100,
		duration: 1,
		onComplete: () => {
			next();
		}
	});
})
</script>

<style lang="scss" scoped>
	.box {
		background-color: red;
	}
</style>
