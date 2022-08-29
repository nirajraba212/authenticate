<template>
  <div id="googleAuthDemo">
    <div>
      <h1>Google Auth</h1>
      <GoogleAuth
        :config="authConfig"
        @authInitialized="authInitialized"
        ref="authRef"
      />
      
    </div>
  </div>
</template>

<script>
import GoogleAuth from "./GoogleAuth.vue";
export default {
  name: "GoogleAuthDemo",
  components: { GoogleAuth },
  data: function() {
    return {
      accessToken: null,
      initialized: false,
      authConfig: {
        apiKey: "AIzaSyBSI6J62iY7QMSErhw_QumFprwWzQFv8XQ",
        discoveryDocs: [],
        clientId:
          "705476648316-fba0luj0192jaombs8p9a54nf20tvod5.apps.googleusercontent.com",
        scopes: "https://www.googleapis.com/auth/userinfo.email",
        plugin_name: "Google Login"
      }
    };
  },
  methods: {
    authInitialized() {
      this.initialized = true;
    },
    // async login() {
    //   this.accessToken = await this.$refs.authRef.login();
    //   console.log(this.accessToken);
    // },
    // async logout() {
    //   await this.$refs.authRef.logout();
    //   this.accessToken = null;
    // }
  }
};
</script>
