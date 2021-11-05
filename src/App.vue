<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />

        Prueba 1 atlantia
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="https://www.linkedin.com/in/leonardo-ibarra-784b7a1b4/"
        target="_blank"
        text
      >
        <span class="mr-2">Linkedin</span>
        <v-icon>open_in_new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  data: () => ({
    //
  }),
};
</script>
