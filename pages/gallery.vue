<template>
  <div>
    <h1>ГАЛЕРЕЯ</h1>
    <v-row>
      <v-col v-for="n in 15" :key="n" class="d-flex child-flex" cols="4">
        <v-img
          :src="`https://picsum.photos/1000/800?image=${n * 2 + 11}`"
          :lazy-src="`https://picsum.photos/10/6?image=${n * 2 + 11}`"
          aspect-ratio="1"
          class="grey lighten-2"
        >
          <template v-slot:placeholder>
            <v-row class="fill-height ma-0" align="center" justify="center">
              <v-progress-circular
                indeterminate
                color="grey lighten-5"
              ></v-progress-circular>
            </v-row>
          </template>
        </v-img>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  name: "gallery",
};
</script>

<style></style>
