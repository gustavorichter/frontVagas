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
			ativo: false
		};
	},
	methods: {
		handleSubmit(event) {
			event.preventDefault();

			const apiKey = '862a2f7d-a9a4-488a-a3d8-299e9875df7es'; // Substitua pela sua chave de API
			const url = 'http://localhost:9090/api/novaVaga';

			const data = {
				titulo: this.titulo,
				descricao: this.descricao,
				ativo: this.ativo
			};
			console.log(data)

			const headers = new Headers();
			headers.append('Content-Type', 'application/json');
			headers.append('X-Api-Key', apiKey);

			const requestOptions = {
				method: 'POST',
				headers: headers,
				body: JSON.stringify(data)
			};

			fetch(url, requestOptions)
				.then(response => {
					// Verifica se a resposta da API está OK
					if (response.ok) {
						// Converte a resposta para JSON
						return response.json();
					} else {
						// Trata erros de resposta da API
						throw new Error('Erro na resposta da API');
					}
				})
				.then(data => {
					// Manipule os dados da resposta da API
					console.log(data);
				})
				.catch(error => {
					// Trata erros na chamada da API
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
