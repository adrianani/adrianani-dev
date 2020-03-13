<template>
	<div class="articles">
		<Article v-for="item in itemsList" :key='item.id' :data='item' />
	</div>
</template>

<script>
import Article from './Article';
import slugify from 'slugify';

export default {
	name: 'Articles',
	components: {
		Article
	},
	data() {
		const images = require.context('../assets/', false, /\.png$/),
			items = [
				{
					id: 1584024662,
					name: 'Automatic social promotion',
					tags: ['php', 'oop', 'html', 'css', 'ipb extension'],
					desc: `an invision power extension meant to automate the social option which the platform already offers.`,
				},
				{
					id: 1584029544,
					name: 'Forum custom reactions',
					tags: ['php', 'oop', 'html', 'css', 'ipb extension'],
					desc: `an extension for ipb which let's administrators set custom reactions for their forums.`,
				},
				{
					id: 1584113072, 
					name: 'Hidden attachments',
					tags: ['php', 'oop', 'html', 'css', 'ipb extension'],
					desc: `this ipb extension enables moderators to hide attachments from public users.`,
				},
				{
					id: 1584113073, 
					name: 'Sidebar discord server',
					tags: ['php', 'oop', 'html', 'css', 'api', 'json', 'ipb extension'],
					desc: `fetches server data from discord's API and displays it as a sidebar widget with much beauty. 💖`,
				},
				{
					id: 1584113074, 
					name: 'Sidebar steam group',
					tags: ['php', 'oop', 'html', 'css', 'api', 'xml', 'ipb extension'],
					desc: `allows administrators to add in the sidebar a widget showing information about a steam group.`,
				},
			].map((val) => {
				const slug = slugify(val.name, {lower: true});
				return {
					...val,
					slug,
					url: `${slug}-${val.id}`,
					image: images(`./${slug}.png`),
				}
			});
		return {items};
	},
	computed: {
		itemsList() {
			if(this.$route.name == 'filter') {
				return this.items.filter((item) => item.tags.includes(this.$route.params.filter) );
			}

			return this.items;
		}
	},
}
</script>