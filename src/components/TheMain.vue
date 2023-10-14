<template>
	<h1 class="center-align">NEWS LIST</h1>
	<AppNews :news="news" v-if="news.length" />
	<AppPreloader v-else />
</template>

<script>
import AppNews from "@/components/AppNews.vue";
import AppPreloader from "@/components/AppPreloader.vue";

export default {
	props: {
		news: {
			type: Array,
			required: true,
		},
	},
	components: {
		AppNews,
		AppPreloader,
	},
};
</script>

<style lang="scss" scoped></style>
