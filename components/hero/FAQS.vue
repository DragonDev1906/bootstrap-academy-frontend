<template>
	<section class="container">
		<SectionTitle
			full
			center
			subheading="Subheadings.HeroFAQS"
			heading="Headings.HeroFAQS"
			body="Body.HeroFAQS"
			class="max-w-2xl mx-auto mb-card"
		/>

		<FAQ
			v-for="({ expand }, i) of faqs"
			:key="i"
			:heading="`List.HeroFAQS.${i + 1}.Heading`"
			:body="`List.HeroFAQS.${i + 1}.Body`"
			:link="i + 1 == 1 ? { to: '/morphcoins', text: 'Links.Here' } : null"
			:expand="expand"
			@expand="setExpand(i, $event)"
		/>
	</section>
</template>

<script>
export default {
	setup() {
		const faqs = ref([
			{ expand: false },
			{ expand: true },
			{ expand: false },
			{ expand: false },
			{ expand: false },
		]);

		function setExpand(index, value) {
			if (!!value) {
				for (let i = 0; i < faqs.value.length; i++) {
					faqs.value[i].expand = i == index;
				}
			}
		}

		return { faqs, setExpand };
	},
};
</script>

<style lang="scss" scoped></style>
