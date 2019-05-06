<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md6>
      <v-btn @click.prevent="getToken" small color="primary">Get Token</v-btn>
    </v-flex>
  </v-layout>
</template>

<script>
import Logo from "~/components/Logo.vue";
import VuetifyLogo from "~/components/VuetifyLogo.vue";
import axios from "axios";
import url from "url";

export default {
  components: {
    Logo,
    VuetifyLogo
  },
  methods: {
    getToken() {
      axios({
        url: "/oauth2/token",
        baseURL: "https://api-users.auth.eu-west-2.amazoncognito.com",
        method: "POST",
        params: {
          grant_type: "client_credentials"
        },
        auth: {
          username: "7lr2840j2432hq7rfclvnnq4de",
          password: "1lqgk7768r2alavhkhvtldndcim1opi1l2fjcqtrop7446r3dan2"
        },
        headers: {
          "Content-Type": "application/x-www-form-urlencoded"
        }
      })
        .then(res => {
          console.log(res);
        })
        .catch(e => {
          console.log(e);
        });

      // this.$axios.$post(
      //   "https://api-users.auth.eu-west-2.amazoncognito.com/oauth2/token?grant_type=client_credentials"
      // );
    }
  }
};
</script>
