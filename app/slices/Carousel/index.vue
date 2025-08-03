<script setup lang="ts">
import type { Content } from "@prismicio/client";
import { Carousel, Slide, Navigation as CarouselNavigation,  Pagination as CarouselPagination  } from "vue3-carousel";
import "vue3-carousel/dist/carousel.css";

defineProps(
  getSliceComponentProps<Content.ImagesCarouselSlice>([
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
  	<div class="carousel_content wrapper">
	  <div class="carousel_content_headlines">
		<div class="carousel_content_title">
			<PrismicRichText :field="slice.primary.title" />
		</div>
		<p class="carousel_content_subtitle">
			{{ slice.primary.subtitle }}
		</p>
	</div>

	<div>
		<PrismicRichText :field="slice.primary.description" />
	</div>
	<div class="carousel_content_container">
		<Carousel
			:items-to-show="2"
			:wrap-around="true"
			:autoplay="0"
			:pause-autoplay-on-hover="true"
			:mouse-drag="true"
			:gap="16"
			:breakpoints="{
				0: { itemsToShow: 1 },
				768: { itemsToShow: 2 },
				1024: { itemsToShow: 3 }
			}"
		  >
			<Slide v-for="(item, index) in slice.primary.carousel_item" :key="index">
			  <div class="carousel_content_item">
				<PrismicImage :field="item.image" class="carousel_content_image"/>
				<div class="carousel_content_item_infos">
					<PrismicRichText :field="item.title" />
					<PrismicRichText :field="item.description" />
				</div>
			  </div>
			</Slide>
			<template #addons>
   				<CarouselNavigation />
				<CarouselPagination />
  			</template>
		  </Carousel>
	</div>
  	</div>
  </section>
</template>

<style scoped>
.carousel_content{
	font-family: system-ui, sans-serif;
	color: #333;
	display: flex;
	flex-direction: column;
	gap: 2rem;
}
.carousel_content *{
	margin: 0;
}
.wrapper{
	padding: 2rem;
	width: 100%;
	max-width: 1016px;
	margin: 0 auto;
	box-sizing: border-box;
}
.carousel_content_headlines{
	display: flex;
	flex-direction: column;
	gap: 0.5rem;
}
.carousel_content_headlines::after{
	content: "";
	width: 4rem;
	height: 2px;
	background-color:#276a60;
	margin-top: 8px;
}
.carousel_content_title{
	font-family: "Libre Baskerville", serif;
	font-size: 1.5em;
}
.carousel_content_subtitle{
	font-size: 1.15rem;
  	font-weight: 500;
	color: #276a60;
}

.carousel_content_container{
	border-radius: 16px;
	padding: 1rem 0;
	overflow: visible;
	position: relative;
}
.carousel_content_item{
	position: relative;
	width: 100%;
	height: 300px;
	border-radius: 8px;
	overflow: hidden;
	box-shadow: 0px 2px 6px 0px rgb(51, 51, 51, 0.25);
}
.carousel_content_image{
	width: 100%;
	height: 300px;
	object-fit: cover;
}
.carousel_content_item_infos{
	position: absolute;
	bottom: 0;
	left: 0;
	width: 100%;
	padding: 1rem;
	box-sizing: border-box;
	display: flex;
	flex-direction: column;
	gap: 0.25rem;
	color: #fff;
	background: linear-gradient(0deg,rgba(0, 0, 0, 1) 0%, rgba(0, 0, 0, 0) 100%);	
}

@media (min-width: 425px) {
  .wrapper {
    padding: 3rem 4rem;
  }
}

:deep(.carousel__next){
	color: #333;
	transform: translateX(2.5rem);
}
:deep(.carousel__prev) {
	color: #333;
	transform: translateX(-2.5rem);
}
:deep(.carousel__pagination) {
	width: 100%;
	left: 0;
	transform: translateY(2.5rem);
}

:deep(.carousel__pagination-button) {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background-color: #ccc;
  transition: background-color 0.3s;
}
:deep(.carousel__pagination-button--active) {
  background-color: #276a60;
}
</style>