<template>
  <v-card class="mx-auto" min-height="150" elevation="7" max-width="350">
    <img :src="article.preview_image" alt="" />
    <!-- ТУТ НАДО СДЕЛАТЬ ПУТЬ К КАРТИНКЕ -->
    <v-card-text>
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
        Перейти
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
