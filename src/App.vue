<template>
	<div>
		<form @submit.prevent="submitForm">
			<Input placeholder="Digite seu nome" v-model="name" />
			<Input placeholder="Digite seu e-mail" v-model="email" />
			<Button @click="submitForm">Enviar</Button>
		</form>
	</div>
</template>

<script>
import Input from './components/Input.vue';
import Button from './components/Button.vue';

export default {
	name: 'App',
	components: {
		Input,
		Button
	},
	data() {
		return {
			name: '',
			email: '',
		};
	},
	methods: {
		submitForm() {
			// Lógica para enviar o formulário
			console.log('Formulário enviado!');
		}
	}
}
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}
</style>
