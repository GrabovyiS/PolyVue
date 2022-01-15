<template>
  <v-row>
    <v-col
      cols="12"
      sm="4"
      v-for="article in articles"
      :key="article.id"
      class="text-center"
    >
      <TheArticle :article="article" />
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: "ArticlesPage",
  data() {
    return {
      articles: [],
    };
  },
  created() {
    fetch("http://demo-api.vsdev.space/api/articles")
      .then((response) => response.json())
      .then((data) => {
        this.articles = data;
      })
      .catch((error) => console.log(error));
  },
};
</script>
