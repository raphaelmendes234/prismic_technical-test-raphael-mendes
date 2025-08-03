<script setup lang="ts">
import type { Content } from "@prismicio/client";

// The array passed to `getSliceComponentProps` is purely optional.
// Consider it as a visual hint for you when templating your slice.
defineProps(
  getSliceComponentProps<Content.FaqSlice>([
    "slice",
    "index",
    "slices",
    "context",
  ]),
);

// Index de l'élément actuellement ouvert (-1 = aucun)
const activeIndex = ref<number | null>(null);
// Toggle l'item cliqué
const toggleAccordion = (index: number) => {
  activeIndex.value = activeIndex.value === index ? null : index;
};
</script>

<template>
  <section
    :data-slice-type="slice.slice_type"
    :data-slice-variation="slice.variation"
  >

  	<div class="faq_content wrapper">
		<div class="faq_content_headlines">
			<div class="faq_content_title">
				<PrismicRichText :field="slice.primary.title" />
			</div>
			<p class="faq_content_subtitle">
				{{ slice.primary.subtitle }}
			</p>
		</div>

		<div class="faq_content_accordion_container">
			<div v-for="(item, index) in slice.primary.item" :key="index" class="faq_content_accordion_item">
			  <button class="faq_content_accordion_button" :class="{ active: activeIndex === index }" @click="toggleAccordion(index)">
				 <PrismicRichText :field="item.question" />
			   </button>
			   <div class="faq_content_accordion_content" :class="{ open: activeIndex === index }">
					<PrismicRichText :field="item.answer" />
			   </div>
		 </div>
		</div>
	</div>
  </section>
</template>


<style scoped>
.faq_content{
	font-family: system-ui, sans-serif;
	color: #333;
	display: flex;
	flex-direction: column;
	gap: 2rem;
}
.faq_content *{
	margin: 0;
}
.wrapper{
	padding: 2rem;
	width: 100%;
	max-width: 1016px;
	margin: 0 auto;
	box-sizing: border-box;
}
.faq_content_headlines{
	display: flex;
	flex-direction: column;
	gap: 0.5rem;
}
.faq_content_headlines::after{
	content: "";
	width: 4rem;
	height: 2px;
	background-color:#276a60;
	margin-top: 8px;
}
.faq_content_title{
	font-family: "Libre Baskerville", serif;
	font-size: 1.5em;
}
.faq_content_subtitle{
	font-size: 1.15rem;
  	font-weight: 500;
	color: #276a60;
}

.faq_content_accordion_item {
	border-radius: 8px;
    border-bottom: 1px solid #e0e0e0;
}
.faq_content_accordion_button {
	background: none;
    border: none;
    width: 100%;
    text-align: left;
    padding: 1rem 2rem;
    font-size: 1.1rem;
    font-weight: bold;
	border-radius: 8px;
    cursor: pointer;
    position: relative;
    transition: all 0.5s ease-in-out;
}

.faq_content_accordion_button:hover {
    background-color: #eaeff2;
}

.faq_content_accordion_button::after {
    content: '';
	width: 8px;
	height: 8px;
    position: absolute;
	top: calc(50% - 4px);
    left: 0.75rem;
    font-size: 1.2rem;
	line-height: 1;
	border-radius: 100%;
	background-color: #276a60;
    transition: all 0.3s ease-in-out;
}
.faq_content_accordion_button.active{
	border-radius: 8px 8px 0px 0px;
	/* background-color: #eaeff2; */
}
.faq_content_accordion_button.active::after {
    height: 2px;
	top: calc(50% - 1px);
}

.faq_content_accordion_content {
    height: 0;
    overflow: hidden;
    transition: all 0.4s ease;
    padding: 0 1.5rem;
	border-radius: 0 0 8px 8px;

}

.faq_content_accordion_content p {
    margin: 1rem 0;
}

.faq_content_accordion_content.open {
    padding: 1.5rem 1.5rem;
    height: 375px;
}
@media (min-width: 360px) {
	.faq_content_accordion_content.open {
    	height: 275px; 
	}
}
@media (min-width: 425px) {
  .wrapper {
    padding: 3rem 4rem;
  }
  .faq_content_accordion_content.open {
    height: 275px; 
}
@media (min-width: 540px) {
	.faq_content_accordion_content.open {
    	height: 200px; 
	}
}
@media (min-width: 640px) {
	.faq_content_accordion_content.open {
    	height: 150px; 
	}
}
@media (min-width: 768px) {
	.faq_content_accordion_content.open {
    	height: 125px; 
	}
}
@media (min-width: 1024px) {
	.faq_content_accordion_content.open {
    	height: 75px; 
	}
}
}
</style>