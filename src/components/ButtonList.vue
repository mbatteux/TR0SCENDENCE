<template>
	<div class="button_list">
		<GlowingButton
			v-if="buttons !== undefined && buttons.length > 0"
			v-for="button in buttons.filter((b) => !b.needAuth | store.getters.isAuthenticated)"
			:text="button.text"
			:dest="button.dest"
			/>
	</div>
</template>

<script setup>
import GlowingButton from '@/components/GlowingButton.vue';
import store from '@store';

const props = defineProps([ 'buttons' ]);
</script>

<style scoped>
.button_list {
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
	gap: 2vh;
	align-self: center;
}
</style>
