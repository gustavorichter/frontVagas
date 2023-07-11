<template>
	<div>
		<form class="flex flex-col" @submit="handleSubmit">
			<Input class="my-2.5" variant="primary" placeholder="Titulo" @update:value="titulo = $event" :value="titulo" />
			<Input class="my-2.5" variant="primary" placeholder="Descrição" @update:value="descricao = $event"
				:value="descricao" />
			<Toggle class="my-2.5" v-model="ativo" />
			<Button class="" variant="primary" type="submit">Enviar</Button>
		</form>
	</div>
</template>

<script>
import axios from 'axios';
import Input from './components/Input.vue';
import Button from './components/Button.vue';
import Toggle from './components/Toggle.vue';

export default {
	name: 'App',
	components: {
		Input,
		Button,
		Toggle
	},
	data() {
		return {
			titulo: '',
			descricao: '',
			ativo: 'a'
		};
	},
	methods: {
		handleSubmit(event) {
			event.preventDefault();

			const url = 'http://localhost:9090/api/novaVaga';
			const apiKey = '862a2f7d-a9a4-488a-a3d8-299e9875df7es';

			const data = {
				"titulo": this.titulo,
				"descricao": this.descricao,
				"ativo": this.ativo
			};

			const headers = {
				'Content-Type': 'application/json',
				'X-Api-Key': apiKey,
				'X-Type': 'api'
			};

			axios.post(url, data, { headers })
				.then(response => {
					console.log(response.data);
				})
				.catch(error => {
					console.error(error);
				});

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
