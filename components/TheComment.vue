<template>
  <v-card width="350" outlined>
    <v-list-item three-line>
      <v-list-item-content>
        <div class="text-overline mb-4 sent author">
          Отправлено: {{ comment.created_at }}
        </div>
        <v-list-item-title class="text-h5 mb-1 comment">
          {{ comment.comment }}
        </v-list-item-title>
        <v-list-item-subtitle>{{ comment.user_name }}</v-list-item-subtitle>
      </v-list-item-content>
    </v-list-item>
  </v-card>
</template>

<script>
export default {
  name: "TheComment",
  props: ["comment"],
  data: () => ({
    selected: [2],
  }),
};
</script>

<style>
.sent.author {
  font-size: 9px !important;
  margin-bottom: 0 !important;
}
.comment {
  text-overflow: initial !important;
  white-space: normal !important;
}
</style>
