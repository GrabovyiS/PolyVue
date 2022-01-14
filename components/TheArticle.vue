<template>
  <v-card class="mx-auto" max-width="344">
    <v-card-text>
      <div>СТАТЬЯ)</div>
      <p class="text-h4 text--primary">{{ article.name }}</p>
      <div class="text--primary">
        {{ article.shortDesc }}
      </div>
    </v-card-text>
    <v-card-actions>
      <v-btn
        :to="{ name: 'articles-id', params: { id: article.id } }"
        text
        color="teal accent-4"
      >
        Перейти)
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  name: "TheArticle",
  props: ["article"],
  data: () => ({}),
};
</script>

<style>
.v-card--reveal {
  bottom: 0;
  opacity: 1 !important;
  position: absolute;
  width: 100%;
}
</style>
