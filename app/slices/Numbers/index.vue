<script setup lang="ts">
import type { Content } from "@prismicio/client";

// The array passed to `getSliceComponentProps` is purely optional.
// Consider it as a visual hint for you when templating your slice.
defineProps(
  getSliceComponentProps<Content.AveragePriceSlice>([
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
	class="blue"
  >
	<div class="price-details_content wrapper">
		<div class="price-details_content_headlines">
			<div class="price-details_content_title">
				<PrismicRichText :field="slice.primary.title" />
			</div>
			<p class="price-details_content_subtitle">
				{{ slice.primary.subtitle }}
			</p>
		</div>

		<div>
			<PrismicRichText :field="slice.primary.description" />
		</div>

		<div class="price-details_content_items-container">
			<div v-for="item in slice.primary.price" class="price-details_content_item">
				<PrismicImage :field="item.icon" class="price-details_content_item_icon" />
				<div>
					<PrismicRichText :field="item.title" />
				</div>
				<div class="price-details_content_item_price">
					<p>{{ item.price }} {{ item.unitd }}</p>
				</div>
				<div>
					<PrismicRichText :field="item.description" />
				</div>
			</div>
		</div>
	</div>
  </section>
</template>

<style scoped>
.blue{
	background-color: #eaeff2;
}
.price-details_content{
	font-family: system-ui, sans-serif;
	color: #333;
	display: flex;
	flex-direction: column;
	gap: 2rem;
}
.price-details_content *{
	margin: 0;
}
.wrapper{
	padding: 2rem;
	width: 100%;
	max-width: 1016px;
	margin: 0 auto;
	box-sizing: border-box;
}
.price-details_content_headlines{
	display: flex;
	flex-direction: column;
	gap: 0.5rem;
}
.price-details_content_headlines::after{
  content: "";
  width: 4rem;
  height: 2px;
  background-color:#276a60;
  margin-top: 8px;
}
.price-details_content_title{
	font-family: "Libre Baskerville", serif;
	font-size: 1.5em;
}
.price-details_content_subtitle{
	font-size: 1.15rem;
  	font-weight: 500;
	color: #276a60;
}

.price-details_content_items-container{
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
	gap: 1rem;
}
.price-details_content_item{
    width: 100%;
    padding: 2rem;
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
	justify-content: center;
	align-items: center;
    gap: 0.5rem;
    border: 1px solid #333;
    border-radius: 8px;
	box-shadow: 0px 2px 6px 0px rgb(51, 51, 51, 0.25);
	transition: all 0.25s ease-in-out;
}
.price-details_content_item:hover{
	transform: scale(0.98);
}
.price-details_content_item_icon{
	width: 48px;
	object-fit: contain;
	object-position: top;
}
.price-details_content_item_price{
	display: flex;
	justify-content: flex-start;
	align-items: flex-end;
	gap: 0.5rem;
	color: #276a60;
	font-size: 1.5rem;
	font-weight: 700;
	line-height: 1;
}

@media (min-width: 425px) {
  .wrapper {
    padding: 3rem 4rem;
  }
}
@media (min-width: 640px) {
  .price-details_content_items-container{
	flex-direction: row;
  }
}
</style>