<template>
	<div class="playboard-selector">
		<h1>Select Playboard</h1>
		<div class="playboard-options">
			<div class="playboard-option" @click="selectMap('map1')">
				<img class="logo" :src="map1Image" alt="Map 1" />
				<p>I</p>
				<p class="dot" v-if="dot === 1">.</p>
			</div>
			<div class="playboard-option" @click="selectMap('map2')">
				<img class="logo" :src="map2Image" alt="Playboard 2" />
				<p>II</p>
				<p class="dot" v-if="dot === 2">.</p>
			</div>
		</div>
	</div>
</template>

<script setup>

import { computed } from 'vue';
import { useStore } from 'vuex'
import map1Image from '@assets/play_boards/map1.png'
import map2Image from '@assets/play_boards/map2.png'

const store = useStore();

const dot = computed(() => {
	return store.state.selected_map === 'map2' ? 2 : 1;
});

const selectMap = (map) => {
	store.commit('changeSelectedMap', map);
}
</script>

<style scoped>
.dot {
	transform: translateY(-5vh);
	font-size: 5vh;
}

#settings_graphics {
	display: flex;
	flex-direction: column;
	height: 100vh;
}

h1 {
	letter-spacing: 0.5em;
}

.playboard-selector {
	text-align: center;
	font-family: 'SpaceTron', sans-serif;
	padding: 10px;
	color: var(--glow-color);
	border: 5px solid var(--glow-color);
	margin: 3vw;
	border-radius: 0.45em;
	-webkit-box-shadow: inset 0px 0px 0.5em 0px var(--glow-color),
		0px 0px 0.5em 0px var(--glow-color);
	-moz-box-shadow: inset 0px 0px 0.5em 0px var(--glow-color),
		0px 0px 0.5em 0px var(--glow-color);
	box-shadow: inset 0px 0px 0.5em 0px var(--glow-color),
		0px 0px 0.5em 0px var(--glow-color);
	-webkit-text-shadow: 0 0 0.125em hsl(0 0% 100% / 0.3),
		0 0 0.45em var(--glow-color);
	-moz-text-shadow: 0 0 0.125em hsl(0 0% 100% / 0.3),
		0 0 0.45em var(--glow-color);
	text-shadow: 0 0 0.125em hsl(0 0% 100% / 0.3), 0 0 0.45em var(--glow-color);
}

.playboard-options {
	display: flex;
	gap: 200px;
	justify-content: center;
}

.playboard-option {
	max-height: 40vh;
	border: 5px solid var(--glow-color);
	border-radius: 8px;
	padding: 16px;
	margin: 8px;
	cursor: pointer;
	transition: transform 0.2s;
	-webkit-box-shadow: inset 0px 0px 0.5em 0px var(--glow-color),
		0px 0px 0.5em 0px var(--glow-color);
	-moz-box-shadow: inset 0px 0px 0.5em 0px var(--glow-color),
		0px 0px 0.5em 0px var(--glow-color);
	box-shadow: inset 0px 0px 0.5em 0px var(--glow-color),
		0px 0px 0.5em 0px var(--glow-color);
}

.playboard-option:hover {
	transform: scale(1.05);
}

.playboard-option img {
	width: 20vw;
	height: 25vh;
}

.title2 {
	margin: 0;
}

p {
	font-size: x-large;
}

.logo {
	filter: var(--image-filter);
}
</style>
