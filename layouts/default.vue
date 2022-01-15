<template>
  <v-app dark>
    <nav>
      <img
        src="https://png2.cleanpng.com/sh/e0c3d5f8d46775e699cd4a30d22ff30e/L0KzQYm3UsA1N5Jsj5H0aYP2gLBuTf1ia5pzjNH8aD3wcbS0jCMugF5xgdH3LX3kc7F6Tf1ia5N0h902b4DogrL7if5oNaRARdN5cHzoPb32hB8uPZI8T9MCNkK2R4i6VcMvPmE8TKI8NEO0RYKAV8kyOGg5SqQCMT7zfri=/kisspng-macintosh-mac-os-x-lion-macos-macbook-operating-sy-apple-logo-5a77a762377353.6074034315177910742271.png"
        alt=""
        id="logo"
      />
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
  border-radius: 50%;
  background-color: rgb(255, 255, 255);
  padding: 5px;
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
