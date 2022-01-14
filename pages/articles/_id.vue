<template>
  <div>
    <v-sheet
      v-if="isLoading"
      :color="`grey ${theme.isDark ? 'darken-2' : 'lighten-4'}`"
    >
      <v-skeleton-loader
        :tile="false"
        max-width="1920"
        type="card"
      ></v-skeleton-loader>
    </v-sheet>
    <div v-else>
      <h1>{{ article.name }}</h1>
      <p>{{ article.desc }}</p>
      <p>
        <em>{{ article.date }}</em>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      article: null,
      isLoading: null,
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
  },
};
</script>
