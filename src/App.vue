<script setup>
// TODO: "select-none"
// I've used "select-none" class quite a few times throughout the application
// goota find and remove it from all those files and apply it here

import TheSettingsModal from '@/components/TheSettingsModal.vue';

import { useStore } from 'vuex';

const store = useStore();

window.songControls.songStateHasBeenUpdated((event, args) => {
	store.dispatch('setCurrentSongState', {
		isLoading: args[0] == 'loading' ? true : false,
		isPlaying: args[1]
	});
});
</script>


<template>
	<div class="app relative">
		<TheSettingsModal v-if="store.state.modal" />
		<router-view />
	</div>
</template>


<style>
@import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Mono&display=swap');

.app {
	font-family: 'IBM Plex Mono', monospace;
}
</style>
