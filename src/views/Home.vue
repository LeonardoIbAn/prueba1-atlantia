<template>
  <v-container fill-height style="max-width: 50%">
    <v-flex>
      <h2>Obten el link secreto introduciendo la clave: Pm7EMK6Cfp9gn568</h2>
      <v-card elevation="2" outlined class="mx-auto">
        <v-text-field
          v-model="clave"
          class="ma-4"
          label="Introduzca la clave"
          required
        ></v-text-field>
        <a v-bind:href="linkSuperSecreto" v-if="linkSuperSecreto">Link super secreto</a>
        
        <v-btn class="ma-4" @click="pedirToken" color="info"> submit </v-btn>
        <v-btn @click="clear" class="ma-4" > clear </v-btn>
        <v-btn @click="pedirSuperSecret" class="ma-4" v-if="token" color="success"> Super Secret </v-btn>
        <v-btn class="ma-4" disabled v-else> Super Secret </v-btn>
      </v-card>
    </v-flex>
  </v-container>
</template>

<script>
import axios from "axios";
export default {
  data: () => ({
    clave: "",
    token: "",
    linkSuperSecreto: ""
  }),

  methods: {
    pedirToken() {
      let me = this;
      const params = JSON.stringify({
        authuser: this.clave,
      });

      axios
        .post("auth", params, {
          headers: {
            "content-type": "application/json",
          },
        })
        .then((response) => {
          me.token = response.data.token;

          console.table(me.token);
          me.clear();
        });
    },
    pedirSuperSecret() {
      let me = this;
      let token = this.token
      const config = {
        headers: { Authorization: `Bearer ${token}` },
      };
      console.log(token)
      axios
        .post("profile",{}, config)
        .then((response) => {
          me.linkSuperSecreto = response.data.SuperSecret;

          console.log(me.linkSuperSecreto);
          //console.log(response.data);
          
        });
    },
    clear() {
      this.clave = "";
    },
  },
};
</script>
