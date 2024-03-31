<template>
	<div class="bg-gray-100">
		<section class="py-10 md:py-16">
			<div class="container max-w-screen-xl mx-auto px-4">
				<nav class="flex items-center justify-between mb-40">
					<!-- <img src="" alt="Logo" /> -->
					<div class="text-xl font-semibold">GAF</div>
					<div class="flex items-center justify-between gap-4">
						<el-input
							v-model="username"
							style="height: 58px; width: 400px"
							placeholder="User Nick"
						/>
						<button
							@click="getInfoUsers"
							class="px-7 py-3 md:px-9 md:py-4 bg-white font-medium md:font-semibold text-gray-700 text-md rounded-md hover:bg-gray-700 hover:text-white transition ease-linear duration-500"
						>
							Search
						</button>
					</div>

					<button
						class="px-7 py-3 md:px-9 md:py-4 bg-white font-medium md:font-semibold text-gray-700 text-md rounded-md hover:bg-gray-700 hover:text-white transition ease-linear duration-500"
					>
						Copy CV
					</button>
				</nav>

				<div v-if="results" class="text-center">
					<div class="flex justify-center mb-16">
						<img
							class="rounded-full"
							v-if="results.avatar_url"
							:src="results.avatar_url"
						/>
					</div>

					<h6
						v-if="results.name"
						class="font-medium text-gray-600 text-lg md:text-2xl uppercase mb-8"
					>
						{{ results.name }}
					</h6>

					<h1
						v-if="results.bio"
						class="font-normal text-gray-900 text-2xl md:text-3xl leading-none mb-8"
					>
						{{ results.bio }}>>
					</h1>

					<p class="font-normal text-gray-600 text-md md:text-xl mb-16">
						<span v-if="results.location">{{ results.location }}</span>
					</p>

					<a
						href="#"
						class="px-7 py-3 md:px-9 md:py-4 font-medium md:font-semibold bg-gray-700 text-gray-50 text-sm rounded-md hover:bg-gray-50 hover:text-gray-700 transition ease-linear duration-500"
						>Hire me</a
					>
				</div>
			</div>
		</section>
	</div>
</template>

<script setup>
import axios from 'axios';
import { onMounted, ref, registerRuntimeCompiler } from 'vue';

let username = ref('nureekdevell');

let URL = 'https://api.github.com/users/';
let results = ref(null);

const getInfoUsers = async () => {
	await axios
		.get(URL + username.value)
		.then(response => {
			results.value = response.data;
		})
		.catch(error => {});
};
</script>

<style scoped></style>
