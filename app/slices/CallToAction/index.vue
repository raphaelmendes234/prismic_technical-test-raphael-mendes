<script setup lang="ts">
import type { Content } from "@prismicio/client";

// The array passed to `getSliceComponentProps` is purely optional.
// Consider it as a visual hint for you when templating your slice.
defineProps(
  getSliceComponentProps<Content.CallToActionSlice>([
    "slice",
    "index",
    "slices",
    "context",
  ]),
);
</script>

<template>
  <section
    :data-slice-type="slice.slice_type"
    :data-slice-variation="slice.variation"
  >

	  <div class="cta_content wrapper">
		<div class="cta_content_container">
			<PrismicImage :field="slice.primary.image" class="cta_content_image"/>
			  <div class="cta_content_infos">
				  <div class="cta_content_title">
					  <PrismicRichText :field="slice.primary.title" />
				  </div>
				  <div class="cta_content_description">
					  <PrismicRichText :field="slice.primary.description" />
				  </div>
				  <button class="cta_content_button">
					  <PrismicLink :field="slice.primary.buttonlink" />
					  <svg xmlns="http://www.w3.org/2000/svg" height="20px" viewBox="0 -960 960 960" width="24px" fill="#ffffff"><path d="M647-440H160v-80h487L423-744l57-56 320 320-320 320-57-56 224-224Z"/></svg>
				  </button>
			  </div>
		</div>
	  </div>
  </section>
</template>

<style scoped>
.cta_content{
	font-family: system-ui, sans-serif;
	color: #333;
}
.cta_content *{
	margin: 0;
}
.wrapper{
	padding: 2rem;
	width: 100%;
	max-width: 1016px;
	margin: 0 auto;
	box-sizing: border-box;
}
.cta_content_container{
	background-color: #eaeff2;
	border-radius: 16px;
	overflow: hidden;
	display: flex;
	flex-direction: column;
	box-shadow: 0px 2px 6px 0px rgb(51, 51, 51, 0.25);
}
.cta_content_image{
	width: 100%;
	height: 200px;
	object-fit: cover;
}
.cta_content_infos{
	width: 100%;
	padding: 2rem;
	box-sizing: border-box;
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
	gap: 1rem;
	text-align: center;
}
.cta_content_title{
	font-family: "Libre Baskerville", serif;
	font-size: 1.5em;
}
.cta_content_button{
	padding: 1rem;
	display: flex;
	justify-content: center;
	align-items: center;
	gap: 0.25rem;
	outline: none;
	border: none;
	border-radius: 8px;
	background-color: #276a60;
	margin-top: 1rem;
	transition: all 0.25s ease-in-out;
}
.cta_content_button:hover{
	cursor: pointer;
	transform: scale(0.98);
	background-color: #1d534b;
}
.cta_content_button a{
	font-size: 1rem;
	font-weight: 500;
	text-decoration: none;
	color: #fff;
}
@media (min-width: 425px) {
  .wrapper {
    padding: 3rem 4rem;
  }
}
@media (min-width: 768px) {
	.cta_content_container{
		flex-direction: row;
	}
	.cta_content_image{
		width: 30%;
		height: 300px;
	}
	.cta_content_infos{
		padding: 3rem;
		align-items: flex-start;
		text-align: left;
	}
}

</style>