# 🏡 Real Estate Prices in Paris 15 – Prismic + Nuxt.js Demo

This project is a technical test for a Frontend Developer apprentice position at Prismic. It demonstrates the creation of a modular and fully editable **landing page** using **Nuxt.js** and **Prismic Slice Machine**, for a fictional real estate company: RealEstateFrance®.

## 🔗 Live demo : 
👉 Visit the live site on Vercel : https://raphaelmendes-habitat.vercel.app/real-estate-price/paris-15

## 📁 Github Repo : 
👉 Find my Github repository : https://github.com/raphaelmendes234/prismic_technical-test-raphael-mendes

---

- All the content of the page is editable with the Page Builder in Prismic.
- Every Slice is general, so they can be used in diferent page for diferent topics.
- Every Slice is responsive, adapted to desktop and mobile.

---

## 🧠 My Approach :

- First I had to learn how to use **Prismic** : 
    - I watched the video tutorials on the website, read the documentation and started my project by following the Set up guide with **Nuxt.js**.
    - I created a **Prismic** repository and set up my **Nuxt.js** project with **Slice Machine**.
    - Then I started exploring the tool, creating pages, pages types, playing with the template slices, looking how they were made to get comfortable.
- Then, I started to work : I created a new reusable **Page type** for my landing page in **Slice Machine**.
- I created a new page in the **Page builder** with my new type.
- After that, I had to create every **Slice** that would compose my page, this is how I did it :
    - Created a new **Slice** in **Slice Machine**.
    - Added the needed **Fields** to it (Image, RichText, Link...).
    - Added it to my **Page type**.
    - Pushing my change to use the **Slice** in the **Page Builder**.
    - In the **Page Builder**, added the **Slice** to my page and filling it with my content.
    - Then going into my code editor to display the Slice's **Fields** and style it.

---

## 🧩 List of Slices created : 

`LandingPageHero` : The hero section of the landing page with an image, the title of the page and a description.
`Numbers` : A slice that can display numbers, their unit, title and description in little cards.
`Carousel` : A carousel of images with a title and desciption.
`Faq` : A slice to display common questions and their answers in the form of accordions.
`CallToAction` : A slice with an image, a big text and a button that encourages the users to click.

All slices are modular and reusable across other real estate locations.

---

## 🛠️ Structure & Tech Stack

- **Framework** : Nuxt.js
- **CMS** : Prismic + Slice Machine
- **Styling** : CSS3
- **Deployment**: Vercel

---

## 🤖 AI Usage

Chat GPT : 
- To generate the page content
- To create some slices : faq and carousel (to gain time)

---

## 🧪 How to Run Locally

```bash
# Clone the repo
git clone https://github.com/raphaelmendes234/prismic_technical-test-raphael-mendes.git
cd prismic_technical-test-raphael-mendes

# Install dependencies
npm install

# Run the dev server
npm run dev
```
---