<template>
  <v-app>
    <v-card
    color="grey-lighten-4"
    flat
    height="200px"
    rounded="0"
  >
    <v-toolbar density="compact">
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>Title</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
    </v-toolbar>
  </v-card>

  <v-footer class="d-flex flex-column">
    <div class="bg-teal d-flex w-100 align-center px-4">
      <strong>Get connected with us on social networks!</strong>

      <v-spacer></v-spacer>

      <v-btn
        v-for="icon in icons"
        :key="icon"
        class="mx-4"
        :icon="icon"
        variant="plain"
        size="small"
      ></v-btn>
    </div>

    <div class="px-4 py-2 bg-black text-center w-100">
      {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
    </div>
  </v-footer>
  </v-app>
</template>
