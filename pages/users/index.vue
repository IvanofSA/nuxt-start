<template>
	<section>
		<h1>{{pageTitle}}</h1>
		<ul>
			<li v-for="user in users" :key="user.id">
				<a href="#" @click.prevent="openUser(user)">{{user.name}}</a>
			</li>
		</ul>
	</section>
</template>

<script>
	export default {
		async asyncData({$axios}) {
			let users = await $axios.$get('https://jsonplaceholder.typicode.com/users')
			return {users}
		},
		name: "index",
		data() {
			return {
				pageTitle: 'User Page'
			}
		},
		methods: {
			openUser(user) {
				this.$router.push('/users/' + user.id)
			}
		}
	}
</script>

<style scoped>

</style>