<template>
	<div style="margin-top: 25px;">
		<div class="row">
			<div class="input-field col s6">
				<label class="active black-text" for="first_name1">Enter date</label>
				<input class="left-align datepicker" id="first_name1" v-model="dateRange" type="date" placeholder="YYYY-MM-DD" :min="dateR" :max="dateN"/>
			</div>
		</div>
		<div class="row">
				<div class="input-field col s6">
					<label class="active black-text" for="first_name2">Enter title</label>
					<input
						v-model="searchValue"
						id="first_name2"
						type="text"
						class="validate"
						@keydown.enter="getSearch"
					/>
					<button class="waves-effect waves-light btn-small" @click="getSearch">Search</button>
				</div>
		</div>
	</div>
</template>

<script>

export default {
	emits: ["emitOnSearch"],
	mounted() {
		// Инициализируем переменные, чтобы были ограничения по выбору даты, так как апи предоставляет новости только за последний месяц(больше для валидации нужно)
		var dateS = new Date();
		var dateM = (parseInt(dateS.getMonth()) < 10) ? ('0'+dateS.getMonth()) : (dateS.getMonth());
		var dateNow = (parseInt(dateS.getMonth()+1) < 10) ? ('0'+(dateS.getMonth()+1)) : (dateS.getMonth()+1);
		// Переменные для ограничения максимальной даты и минимальной даты
		this.dateR = dateS.getFullYear()+'-'+dateM+'-'+dateS.getDate();
		this.dateN = dateS.getFullYear()+'-'+dateNow+'-'+dateS.getDate();
	},
	data() {
		return {
			searchValue: "Google",
			dateRange: null,
			dateR: '',
			dateN: ''
		};
	},
	methods: {
		getSearch() {
			this.$emit("emitOnSearch", this.searchValue, this.dateRange);
		},
	},
};
</script>

<style lang="scss" scoped></style>
