<template>
  <span>
    <!-- Left empty intentionally -->
  </span>
</template>

<script>
var apiUrl = "https://connect.facebook.net/en_US/sdk.js";

async function initFacebook(appId, component) {
  window.fbAsyncInit = async function() {
    window.FB.init({
      appId: appId,
      cookie: true, // This is important, it's not enabled by default
      version: "v2.2"
    });

    component.$emit("authInitialized");
  };
}

export default {
  name: "FacebookAuth",

  props: {
    appId: null
  },

  created: async function() {
    await this.loadFacebookSDK(document, "script", "facebook-jssdk");
    await initFacebook(this.appId, this);
  },

  methods: {
    async loadFacebookSDK(d, s, id) {
      var js,
        fjs = d.getElementsByTagName(s)[0];
      if (d.getElementById(id)) {
        return;
      }
      js = d.createElement(s);
      js.id = id;
      js.src = apiUrl;
      fjs.parentNode.insertBefore(js, fjs);
    },

    async login() {
      const loginPromise = () => {return new Promise((resolve, reject) => {
        window.FB.login(function(response) {
          if (response.authResponse) {
            if (response.status === "connected") {
              resolve(response.authResponse);
            }
          } else {
            reject("User cancelled login or did not fully authorize.");
          }
        });
      })};
      var result = await loginPromise();
      console.log(result);
      return result;
    },

    async logout() {
      const logoutPromise = () => {return new Promise((resolve) => {
        window.FB.logout(function() {
          resolve();
        });
      })};
      await logoutPromise();
    }
  }
};
</script>
