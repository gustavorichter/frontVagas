<template>
	<input v-bind="$attrs" v-on="$listeners" class="input-component" />
</template>

<script>
	export default {
		name: 'Input',
	};
</script>

<style scoped>
	.input-component {
		/* Estilos do componente de input */
	}
</style>