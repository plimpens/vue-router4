<template>
	<section >
		<h1>{{experience.name}}</h1>
		<div>
			<img :src="`/images/${experience.image}`" :alt="experience.name">
			<p>{{experience.description}}</p>
		</div>
	</section>
</template>

<script>
	import sourceData from '@/data.json'
	
	export default {
		name: "ExperienceShow",
		props: {
			id: {
				type: Number,
				required: true
			},
			experienceSlug: {
				type: String,
				requiered: true
			}
		},
		computed: {
			destination() {
				return sourceData.destinations.find(
					(destination) =>  destination.id === this.id
				)
			},
			experience() {
				return this.destination.experiences.find(
					experience => experience.slug === this.experienceSlug
				)
			}
		},
	}
</script>