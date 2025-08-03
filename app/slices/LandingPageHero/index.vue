<script setup lang="ts">
import type { Content } from "@prismicio/client";

// The array passed to `getSliceComponentProps` is purely optional.
// Consider it as a visual hint for you when templating your slice.
defineProps(
  getSliceComponentProps<Content.TestSlideSlice>([
    "slice",
    "index",
    "slices",
    "context",
  ]),
);
</script>

<template>
  <section :data-slice-type="slice.slice_type" :data-slice-variation="slice.variation">

    <div class="hero_content">
      <div class="hero_content_image-wrapper wrapper">
        <PrismicImage :field="slice.primary.image" class="hero_content_image"/>
      </div>

      <div class="hero_content_headlines wrapper">
        <p class="hero_content_eyebrow">
          {{ slice.primary.eyebrowheadline }}
        </p>
        <div class="hero_content_title">
          <PrismicRichText :field="slice.primary.title"/>
          <div class="hero_content_date">
            <p>{{ slice.primary.date }}</p>
          </div>
        </div>
      </div>
      <div class="hero_content_description">
            <PrismicRichText :field="slice.primary.description" />
      </div>
    </div>
      
  </section>
</template>

<style scoped>
.hero_content {
  font-family: system-ui, sans-serif;
  background-color: #fff;
  color: #333;
  margin: 0;
}
.hero_content *{
  margin: 0;
}
.wrapper{
    padding: 2rem;
    width: 100%;
    max-width: 1016px;
    margin: 0 auto;
    box-sizing: border-box;
}
.hero_content_image-wrapper{
  display: flex;
  justify-content: flex-end;
  align-items: center;
  padding-bottom: 0;
}
.hero_content_image{
	width: 100%;
	height: 400px;
	object-fit: cover;
	border-radius: 8px;
  box-shadow: 0px 2px 6px 0px rgb(51, 51, 51, 0.25);
}
.hero_content_headlines{
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}
.hero_content_headlines::after{
  content: "";
  width: 4rem;
  height: 2px;
  background-color: #276a60;
  margin-top: 8px;
}
.hero_content_eyebrow{
  color: #276a60;
  font-size: 1.15rem;
  font-weight: 500;
  margin: 0;
}
.hero_content_title{
  font-family: "Libre Baskerville", serif;
  font-size: 1.625rem;
  font-weight: 700;
  line-height: 1;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  gap: 1rem;
}
.hero_content_date{
  width: fit-content;
  height: fit-content;
  padding: 0.5rem 0.75rem;
  font-family: system-ui, sans-serif;
  font-size: 0.75rem;
  font-weight: 400;
  color: #276a60;
  background-color: #276a6040;
  border-radius: 8px;
  margin-bottom: 0;
}
.hero_content_description{
  width: 100%;
  max-width: 1016px;
  margin: 0 auto;
  box-sizing: border-box;
  padding: 2rem;
}



@media (min-width: 425px) {
  .wrapper {
    padding: 3rem 4rem;
  }
  .hero_content_image-wrapper{
    padding-bottom: 0;
  }
  .hero_content_title {
    flex-direction: row;
    justify-content: flex-start;
    align-items: flex-end;
  }
  .hero_content_description{
    padding: 0 4rem 4rem 4rem;
  }
}

@media (min-width: 640px) {
  .hero_content_title {
    font-size: 2rem;
  }
  .hero_content_date{
    font-size: 1rem;
    margin-bottom: 0.25rem;
  }
}

@media (min-width: 1024px) {
  .hero_content_title {
    font-size: 2.25rem;
  }
}

@media (min-width: 1200px) {
  .hero_content_title {
    font-size: 2.5rem;
  }
}
</style>