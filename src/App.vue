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

			<el-button type="danger">Search</el-button>
		</div>
	</header>
</template>

<script setup>
import { ref } from 'vue';

let input = ref('');
</script>

<style lang="scss" scoped></style>
