<template>
	<a :href="url" target="_blank" rel="noopener nofollow">
		<FontAwesome :icon="icon" />
		{{name}}
	</a>
</template>

<script>
export default {
	name: 'SocialLink',
	props: {
		url: String,
		icon: [String, Array],
		name: String,
	}
}
</script>