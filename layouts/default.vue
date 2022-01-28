<template>
  <v-app dark>
    <nav>
      <img src="/logo.png" alt="" id="logo" />
      <div id="links">
        <NuxtLink to="/"> Главная </NuxtLink>
        <NuxtLink to="/articles"> Статьи </NuxtLink>
        <NuxtLink to="/gallery"> Галерея </NuxtLink>
      </div>
      <div id="input-container">
        <v-text-field label="Поиск" prepend-icon="mdi-magnify"></v-text-field>
      </div>
    </nav>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "DefaultLayout",
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,

      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: "Vuetify.js",
    };
  },
};
</script>

<style>
nav {
  margin: 0 0 40px 0;
  padding: 10px 30px 10px 10px;
  width: 100vw;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
#logo {
  height: 40px;
  width: 40px;
}
#input-container {
  min-width: 250px;
  padding: 10px;
}
#links {
  width: 210px;
  display: flex;
  justify-content: space-between;
}
#links > a {
  color: white;
  text-decoration: none;
}
</style>
