<template>
	<input :placeholder="placeholder" :value="value" @input="$emit('update:value', $event.target.value)"
		:class="['input', variantClass]" />
</template>

<script>
export default {
	name: 'Input',
	props: {
		placeholder: String,
		value: [String, Number],
	},
	props: {
		variant: {
			type: String,
			default: 'default'
		}
	},
	computed: {
		variantClass() {
			if (this.variant === 'primary') {
				return 'button-primary';
			} else if (this.variant === 'secondary') {
				return 'button-secondary';
			} else if (this.variant === 'accent') {
				return 'button-accent';
			} else {
				return ''; // classe padrão para a variante 'default'
			}
		}
	}
};
</script>