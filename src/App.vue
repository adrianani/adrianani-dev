<template>
  <div id="app">
	<div class="wrapper">
		<Header />
		<div>
			<router-view/>
			<aside class='social'>
				<SocialLink url="https://github.com/adrianani/" name="github" :icon="['fab', 'github']"/>
				<SocialLink url="https://twitter.com/adrianani99" name="twitter" :icon="['fab', 'twitter']"/>
				<SocialLink url="#" name="email" :icon="['fas', 'at']" @click.native="emailClick" />
			</aside>
		</div>
	</div>
  </div>
</template>

<style lang="scss">
	@import '@/styles/global.scss';
</style>

<script>
import Header from '@/components/Header';
import SocialLink from '@/components/SocialLink';

export default {
	name: 'App',
	components: {
		Header,
		SocialLink
	},
	methods: {
		emailClick(e) {
			e.preventDefault();
			const textarea = document.createElement('textarea');
			textarea.value = 'ani.adrian99andrei@gmail.com';
			document.body.appendChild(textarea);
			textarea.select();
			document.execCommand('copy');
			document.body.removeChild(textarea);
		}
	}
}
</script>