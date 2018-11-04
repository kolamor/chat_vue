<template>
	<div>
		<select v-model="option">
			<option v-for="user in list"
			:value="user.id">
			{{ user.attributes.username }}
				
			</option>
		</select>
		<mu-button class="btn-send" round color="success" @click="AddUsers"> Добавить пользователя
		</mu-button>
		
	</div>

</template>

<script>
	
	export default {
		name: "AddUsers",
		data() {
			return {
				options: '',
				list: '',
			}
		},
		created(){
			this.loadUsers()
		},
		methods: {
			// получение списка user
			loadUsers() {
				$.ajax({
					url: "http://127.0.0.1:8000/api/v1/chat/users/",
					type: "GET",
					success: (response) => {
						this.list = response.data
					}
				})
			},
			// добавление user в room
			addUsers(){
				
			}
		}
	}

</script>

<style scoped>

</style>