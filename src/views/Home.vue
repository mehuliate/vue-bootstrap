<template>
  <div class="home">
    <b-container>
		<b-row align-v="center">
			<JobCard v-for="job in displayJob" :key="job.id" :name="job.name"></JobCard>
		</b-row>
		<b-pagination
		v-model="currentPage"
		:total-rows="rows"
		:per-page="perPage"
		first-text="First"
		prev-text="Prev"
		next-text="Next"
		last-text="Last"
		@input="paginate(currentPage)"
		></b-pagination>
      
    </b-container>
  </div>
</template>

<script>
// @ is an alias to /src
import JobCard from "@/components/JobCard.vue";

export default {
	name: "home",
	components: {"JobCard": JobCard },
	mounted(){
		this.fetchData();
	},
	data(){
		return {
			jobs : [],
			displayJob: [],
			currentPage: 1,
			rows:1,
			perPage: 3
		}
	},
	methods: {
		async fetchData(){
			const res = await fetch("data.json");
			const val = await res.json();
			this.jobs = val;
			this.displayJob = val.slice(0,3);
			this.rows = this.jobs.length;
		},
		paginate(currentPage){
			console.log(currentPage);
			const start = (currentPage - 1 ) * this.perPage;
			this.displayJob = this.jobs.slice(start, start+3);
		}
	}
}
</script>
