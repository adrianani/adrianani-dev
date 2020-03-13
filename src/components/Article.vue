<template>
	<article>
		<router-link class="cover" :style="{backgroundImage: `url(${data.image})`}"></router-link>
		<div class="text">
			<router-link class="title">{{data.name}}</router-link>
			<div class="tags">
				<router-link class="tag" v-for='tag in data.tags' :key='tag' :to="{name: 'filter', params: {filter: tag}}" @mouseenter.native="mouseOver" @mouseleave.native="mouseOut">
					{{tag}}
				</router-link>
			</div>
			<div class="desc">{{data.desc}}</div>
		</div>
	</article>
</template>

<script>

export default {
	name: 'Article',
	props: {
		data: Object,
	},
	methods: {
		mouseOver(e) {
			let self = e.currentTarget,
				parent = self.parentElement,
				tags = parent.querySelectorAll('.tag');

			tags.forEach(el => {
				if(el !== self ) {
					el.style.opacity = .4;
				}
			});
		},
		mouseOut(e) {
			let self = e.currentTarget,
				parent = self.parentElement,
				tags = parent.querySelectorAll('.tag');

			tags.forEach(el => {
				if(el !== self) {
					el.style.opacity = 1;
				}
			});
		}
	}
}
</script>