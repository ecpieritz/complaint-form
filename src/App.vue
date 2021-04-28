<template>
	<div id="app">
		<h1>Register Complaint</h1>
		<div class="conteudo">
			<form class="painel">
				<div class="cabecalho">Form</div>
				<Rotulo nome="E-mail">
					<input type="text" v-model.lazy.trim="user.email">
				</Rotulo>
				<Rotulo nome="Password">
					<input type="password" v-model.lazy.trim="user.password">
				</Rotulo>
				<Rotulo nome="Age">
					<input type="number" v-model.number="user.age" min="18" max="115">
				</Rotulo>
				<Rotulo nome="Message">
					<textarea name="" cols="30" rows="5" v-model.lazy.trim="message"></textarea>
				</Rotulo>
				<Rotulo nome="Problem Features">
					<span class="mr-4"><input type="checkbox" value="Reproducible" v-model="features"> Reproducible</span>
					<span><input type="checkbox" value="Intermittent" v-model="features"> Intermittent</span>
				</Rotulo>
				<Rotulo nome="Which product?">
					<span class="mr-4"><input type="radio" v-model="product" value="Web"> Web</span>
					<span class="mr-4"><input type="radio" v-model="product" value="Mobile"> Mobile</span>
					<span><input type="radio" v-model="product" value="Other"> Other</span>
				</Rotulo>
				<Rotulo nome="Priority">
					<select v-model="priority">
						<option v-for="priority in priorities" 
						:key="priority.code"
						:selected="priority.code === 1">{{priority.name}}</option>
					</select>
				</Rotulo>
				<Rotulo nome="First complaint?">
					<Escolha v-model="choice" />
				</Rotulo>
				<hr>
				<button>Send</button>
			</form>
			<div class="painel">
				<div class="cabecalho">Result</div>
				<Rotulo nome="E-mail">
					<span>{{user.email}}</span>
				</Rotulo>
				<Rotulo nome="Password">
					<span>{{user.password}}</span>
				</Rotulo>
				<Rotulo nome="Age">
					<span>{{user.age}}</span>
				</Rotulo>
				<Rotulo nome="Message">
					<span style="white-space: pre;">{{message}}</span>
				</Rotulo>
				<Rotulo nome="Check Options">
					<span>
						<ul>
							<li v-for="f in features" :key="f">{{f}}</li>
						</ul>
					</span>
				</Rotulo>
				<Rotulo nome="Which product?">
					<span>{{product}}</span>
				</Rotulo>
				<Rotulo nome="Priority">
					<span>{{priority}}</span>
				</Rotulo>
				<Rotulo nome="First complaint?">
					<span v-if="choice == true">Yes</span>
					<span v-else>No</span>
				</Rotulo>
			</div>
		</div>
	</div>
</template>

<script>
import Rotulo from './components/Rotulo.vue'
import Escolha from './components/Escolha.vue'

export default {
	name: 'app',
	components: { Rotulo, Escolha },
	data(){
		return {
			user: {
				email: '',
				password: '',
				age: 18,
			},
			message: '',
			features: [],
			product: 'Web',
			priorities: [
				{code: 1, name: 'Low'},
				{code: 2, name: 'Low-medium'},
				{code: 3, name: 'Medium'},
				{code: 4, name: 'Medium-high'},
				{code: 5, name: 'High'}
			],
			priority: 'Low',
			choice: true
		}
	},
}
</script>

<style>

body {
	background-color: #ECECEC;
}

#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;

	display: flex;
	flex-direction: column;
}

.conteudo {
	display: flex;
}

.painel {
	flex: 1;
	background: #FFF;
	margin: 0px 10px;
	padding: 20px;
	border: 1px solid #AAA;
	border-radius: 5px;
}

.painel .cabecalho {
	width: 100%;
	background-color: #DDD;
	padding: 10px 0px;
	border-radius: 5px;
	font-size: 1.4rem;
}

#app form button {
	float: right;
	margin: 10px 0px;
	padding: 10px 20px;
	font-size: 1.4rem;
	border-radius: 5px;
	color: #FFF;
	background-color: #2196F3;
}

#app h1 {
	font-weight: 200;
	margin: 20px;
	padding: 0;
}

.mr-4 {
	margin-right: 40px;
}
</style>
