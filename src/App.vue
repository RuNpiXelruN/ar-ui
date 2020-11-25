<template>
	<div id="app">
		<div class="app-container">
			<Header 
				:count="events.length"
			/>
			<ArUI 
				:events="events"
			/>
		</div>
	</div>
</template>

<script>
import eventData from '@/eventData.json'

import Header from '@/components/Header.vue'
import ArUI from '@/components/ArUI.vue'

export default {
	name: 'App',
		components: {
		Header,
		ArUI
	},
	data() {
		return {
			events: null
		}
	},
	created() {
		this.events = eventData
	}
}
</script>

<style>
@font-face {
    font-family: 'GraphikMedium';
    font-display: swap;
    src: local('Graphik Medium Regular'), 
        url(~@/assets/fonts/Graphik_Medium_Regular.otf) format('otf'),
        url(~@/assets/fonts/Graphik_Medium_Regular.ttf) format('ttf'),
        url(~@/assets/fonts/Graphik_Medium_Regular.woff2) format('woff2');
}
@font-face {
    font-family: 'GraphikRegular';
    font-display: swap;
    src: local('Graphik Regular Regular'), 
        url(~@/assets/fonts/Graphik_Regular_Regular.otf) format('otf'),
        url(~@/assets/fonts/Graphik_Regular_Regular.ttf) format('ttf'),
        url(~@/assets/fonts/Graphik_Regular_Regular.woff2) format('woff2');
}

body {
    margin: 0;
    padding: 0;
    font-family: 'GraphikRegular';
    font-weight: 400;
	background: #F6F9FC;
}

#app {
	font-family: 'GraphikRegular';
    font-weight: 400;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	min-height: 100vh;
	width: 100%;
}

.app-container {
	display: flex;
	flex-flow: column nowrap;
	align-items: center;
	justify-content: center;
	width: 100%;
}
</style>
