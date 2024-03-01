<template>
	<MainPage />
</template>

<script setup>
import MainPage from './components/MainPage.vue'

</script>

<style lang="scss">
@import 'src/assets/scss/variables';

#app {
	min-height: 100vh;
	width: 100%;
	display: flex;
	justify-content: center;
	background-color: $gray;
}
</style>
