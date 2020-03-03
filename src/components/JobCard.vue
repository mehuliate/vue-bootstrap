<template>
    <div>
        <b-col>
			<b-card
				:title="name"
				img-src="https://picsum.photos/600/300/?image=25"
				img-alt="job-info"
				class="mb-3"
				img-top
				tag="article"
				style="max-width: 20rem"
                footer="Card Footer"
			>
				<b-card-text>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Debitis repudiandae possi</b-card-text>
				<b-button
					variant="primary"
				>Apply</b-button>
			</b-card>
		</b-col>

    </div>
</template>

<script>
export default {
    props: ['name']
}
</script>

<style scoped>

</style>