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
    <form id="form" @submit.prevent="send">
      <text-input @textinput="setUserName" :label="'Имя'" />
      <text-input @textinput="setUserComment" :label="'Комментарий'" />
      <v-btn type="submit" elevation="2" outlined>Отправить комментарий</v-btn>
    </form>
    Форма добавления комментария содержит вложенные компоненты text-input и
    должна осуществлять обмен данными между ними (при помощи v-model и $emit)
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
      userName: null,
      userComment: null,
      theme: {
        default: { isDark: false },
      },
    };
  },
  methods: {
    setUserName(prop) {
      this.userName = prop;
    },
    setUserComment(prop) {
      this.userComment = prop;
    },
    send() {
      const sentTime = Date.now();
      const requestOptions = {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
          user_name: this.userName,
          comment: this.userComment,
        }),
      };
      fetch(
        `http://demo-api.vsdev.space/api/articles/${this.$route.params.id}/comments`,
        requestOptions
      );
      this.comments.push({
        created_at: sentTime,
        user_name: this.userName,
        comment: this.userComment,
        id: sentTime,
      });
    },
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
