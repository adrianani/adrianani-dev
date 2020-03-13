<template>
	<article v-html="content" class='article'>
	</article>
</template>
<script>
import MarkdownIt from 'markdown-it';

export default {
	name: 'FullArticle',
	computed: {
		content() {
			const md = new MarkdownIt(), 
				{id, slug} = this.$route.params,
				content = require(`@/assets/articles/a${id}.md`), 
				image = require(`@/assets/${slug}.png`);
			console.log(image);
			return `
				<header style='background-image: url(${image})'></header>
				<main>
					${md.render(content.default)}
				</main>
			`;
		}
	}
}
</script>

