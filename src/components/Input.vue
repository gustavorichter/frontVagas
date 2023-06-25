<template>
	<input
		:placeholder="placeholder"
     	:value="value"
      	@input="$emit('update:value', $event.target.value)"
      	class="input-component"
	/>
</template>

<script>
	export default {
		name: 'Input',
		props: {
			placeholder: String,
			value: [String, Number],
		},
	};
</script>

<style scoped>
	.input-component {
		/* Estilos do componente de input */
	}
</style>