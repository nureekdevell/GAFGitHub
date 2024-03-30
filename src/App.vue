<template>
	<header class="bg-[#F7F6F4] h-screen">
		<div class="container flex justify-center items-center pt-5 gap-5">
			<div>
				<el-input
					v-model="input"
					style="width: 240px"
					placeholder="User Nick"
				/>
			</div>

			<el-button @click="getAvatar" type="danger">Search</el-button>
		</div>
		<div>{{}}</div>
	</header>
</template>

<script setup>
import axios from 'axios';
import { onMounted, ref } from 'vue';
// let githubUrl = `https://avatars.github.com/${input}.png`;

let input = ref('');

const getAvatar = async () => {
	let githubUrl = `https://api.github.com/users/${input}`;
	await fetch(githubUrl)
		.then(res => res.json())
		.then(data => {
			console.log(data);
		})
		.catch(e => {
			console.log(e);
		});
};
</script>

<style lang="scss" scoped></style>
