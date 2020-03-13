<template>
	<header>
		<router-link class="logo" :to="{name: 'home'}">
			<div class="avatar"></div>
			<div class="text">
				<div class="name">
					Adrian Ani
				</div>
				<div class="desc">
					web developer
				</div>
			</div>
		</router-link>
	</header>
</template>

<script>
export default {
	name: 'Header',
}
</script>