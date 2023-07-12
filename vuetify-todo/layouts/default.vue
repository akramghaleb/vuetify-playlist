<template>
    <v-app id="inspire">
        <v-navigation-drawer v-model="drawer">
        <template v-slot:prepend>
            <v-list-item
                lines="two"
                prepend-avatar="https://cdn.vuetifyjs.com/docs/images/logos/vuetify-logo-v3-slim-dark.svg"
                title="Vuetify Todo"
                subtitle="Best to do ever"
            ></v-list-item>
            </template>

            <v-divider></v-divider>

            <v-list density="compact" nav>
            <v-list-item prepend-icon="mdi-home-city" title="Todo" value="todo"></v-list-item>
            <v-list-item prepend-icon="mdi-help-box" title="About" value="about"></v-list-item>
            </v-list>
        
        </v-navigation-drawer>

        <v-app-bar>
        <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

        <v-toolbar-title>Application</v-toolbar-title>
        </v-app-bar>

        <v-main>
        <slot />
        </v-main>
    </v-app>
</template>

<script setup>
import { ref } from 'vue'

const drawer = ref(null)
</script>