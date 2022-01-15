<template>
  <div>
    <h1>ГЛАВНАЯ</h1>
    <v-carousel v-model="model">
      <v-carousel-item v-for="article in slideArticles" :key="article.id">
        <v-sheet :color="colors[article.id - 1]" height="100%" tile>
          <v-row class="fill-height" align="center" justify="center">
            <v-btn
              elevation="24"
              x-large
              :to="{ name: 'articles-id', params: { id: article.id } }"
              >{{ article.name }}</v-btn
            >
          </v-row>
        </v-sheet>
      </v-carousel-item>
    </v-carousel>
  </div>
</template>

<script>
export default {
  name: "IndexPage",
  data: () => ({
    articles: [],
    slideArticles: [],
    model: 0,
    colors: [
      "primary",
      "secondary",
      "yellow darken-2",
      "red",
      "orange",
      "blue",
    ],
  }),
  created() {
    fetch("http://demo-api.vsdev.space/api/articles")
      .then((response) => response.json())
      .then((data) => {
        this.articles = data;
        data.forEach((article) => {
          if (article.slider == true) {
            this.slideArticles.push(article);
          }
        });
      })
      .catch((error) => console.log(error));
  },
};
</script>

<style>
h1 {
  margin-bottom: 40px;
}
</style>
