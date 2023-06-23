<template>
  <nav>
    <v-app-bar flat color="pink-darken-4">
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title class="text-h4">
        <span class="font-weight-light">Workers</span>
        <span>Home</span>
      </v-toolbar-title>
    </v-app-bar>

    <v-navigation-drawer v-model="drawer" app>
      <v-list v-for="link in links" :key="link.title" density="comfortable" nav>
        <v-list-item
          class="d-flex"
          router
          :to="link.route"
          :prepend-icon="link.icon"
        >
          <v-list-item-title>{{ link.title }} </v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      drawer: false,
      links: [
        {
          icon: "mdi-home",
          title: "Главная",
          route: "/",
        },
        {
          icon: "mdi-forum",
          title: "О проекте",
          route: "/about",
        },
      ],
    };
  },
};
</script>
