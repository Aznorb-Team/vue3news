<template>
	<TheHeader />
	
	<div class="container main">
		<AppSearch @emit-on-search="getNewsList"/>
		<TheMain :news="news"/>
	</div>
	
	<TheFooter />
</template>

<script>
import TheHeader from "@/components/TheHeader.vue";
import TheMain from "@/components/TheMain.vue";
import AppSearch from "@/components/AppSearch.vue";
import TheFooter from "@/components/TheFooter.vue";

import axios from "axios";


export default {
	mounted() {
		this.getNewsList();
	},
	components: {
		TheFooter,
		TheHeader,
		TheMain,
		AppSearch,
	},
	data() {
		return {
			news: [],
		};
	},
	methods: {
		async getNewsList(str = 'Google', dateRange = '2023-10-12') {
			try{
				this.isPostLoading = true;
				const response = await axios.get('https://newsapi.org/v2/everything?q='+str+'&from='+dateRange+'&apiKey=82199e1cf5364c3cb68b82bce0dbeb1f');
				this.news= response.data.articles;
			}catch(e){
				console.log(e);
			}
			
		},
		setDate(st){
			this.selectedDate = st;
		}
	},
};
</script>

<style lang="scss"></style>
