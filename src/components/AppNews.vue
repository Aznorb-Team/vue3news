<template>
	<div class="card-news">
		<div class="card hoverable" v-for="nw in news" :key="nw.imdbID">
			<div class="card-image">
				<img :src="nw.urlToImage" />
			</div>
			<div class="card-content">
				<span class="card-title">{{ nw.title }}</span>
				<blockquote >
					{{ nw.description }}
				</blockquote>
				<p class="right-align">{{nw.author}}</p>
				<p class="right-align">{{nw.publishedAt.substring(0,10)}}</p>
			</div>
			<div class="card-action">
				<a class="teal-text" :href="nw.url">Go to news</a>
			</div>
		</div>
	</div>

</template>

<script>
export default {
	props: {
		news: {
			type: Array,
			required: true,
		},
	},
};
</script>

<style lang="scss" scoped></style>
