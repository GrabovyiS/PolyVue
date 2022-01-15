<template>
  <div>
    <v-sheet
      v-if="isLoading"
      :color="`grey ${theme.isDark ? 'darken-2' : 'lighten-4'}`"
    >
      <v-skeleton-loader
        :tile="true"
        class="mx-auto"
        type="article"
        :loading="true"
      ></v-skeleton-loader>
    </v-sheet>
    <div v-else>
      <h1>{{ article.name }}</h1>
      <v-img
        class="image"
        max-height="500"
        :src="'/' + article.full_image"
      ></v-img>
      <p>{{ article.desc }}</p>
      <p>
        <em>{{ article.date }}</em>
      </p>
    </div>
    <!-- ГЫГЫК инпуты для комментариев -->
    <v-row class="comment-row" v-for="comment in comments" :key="comment.id">
      <TheComment :comment="comment" />
    </v-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      article: null,
      isLoading: null,
      comments: null,
      theme: {
        default: { isDark: false },
      },
    };
  },
  created() {
    this.isLoading = true;
    fetch(`http://demo-api.vsdev.space/api/articles/${this.$route.params.id}`)
      .then((response) => response.json())
      .then((data) => {
        this.article = data;
        this.isLoading = false;
      })
      .catch((error) => console.log(error));

    fetch(
      `http://demo-api.vsdev.space/api/articles/${this.$route.params.id}/comments`
    )
      .then((response) => response.json())
      .then((data) => {
        this.comments = data;
      })
      .catch((error) => console.log(error));
  },
};
</script>

<style>
.comment-row {
  margin: 10px;
}
.image {
  margin: 20px 0;
}
</style>
