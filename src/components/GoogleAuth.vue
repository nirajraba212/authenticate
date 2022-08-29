<template>
  <span>
    <!-- Left empty intentionally -->
    <div class="g-signin2" data-onsuccess="onSignIn"></div>
  </span>
</template>

<script>
//var apiUrl = "https://apis.google.com/js/platform.js";

export default {
  name: "GoogleAuth",
  props: {
    config: { type: Object }
    // apiKey: {type: String},
    // discoveryDocs: {type: [String]},
    // clientId: {type: String},
    // scopes: {type: String},
  },
  created: function() {
    
    //this.installClient();
  },
  data: function() {
    return {
      GoogleAuth: null,
      GoogleUser: null
    };
  },

  methods: {
    async login() {
      // if (this.GoogleAuth.isSignedIn.get()) {
      //   this.GoogleUser = this.GoogleAuth.currentUser.get();
      // } else {
      //   this.GoogleUser = await this.GoogleAuth.signIn();
      // }
      // return this.GoogleUser.getAuthResponse().access_token;
    },
    async logout() {
      //await this.GoogleAuth.signOut();
    },
    installClient() {
      // var script = document.createElement("script");
      // script.src = apiUrl;
      // var self = this;
      // script.onreadystatechange = script.onload = function() {
      //   console.log("load",window.gapi);
        
      //   window.gapi.load('auth2', function() {
      //     self.initClient();
      //   });
        
      // };
      // document.getElementsByTagName("head")[0].appendChild(script);
    },
    initClient() {
      //var self = this;
      //if(window.gapi && window.gapi.auth2) {
        //  window.gapi.auth2.init({ client_id: "705476648316-fba0luj0192jaombs8p9a54nf20tvod5.apps.googleusercontent.com" })
        //   .then(function(GoogleAuth) {
        //     console.log("GoogleAuth",GoogleAuth);
        //     GoogleAuth.then(function(onInit,onError){
        //       console.log("onInit",onInit);
        //       console.log("onError",onError);
        //       //self.GoogleAuth = window.gapi.auth2.GoogleAuth;
        //       //self.$emit("authInitialized");
        //     });
            
        //   })
        //   .catch(error => {
        //     console.log(error);
        //   });
      //}
      
    },
    onSignIn(googleUser) {
      var profile = googleUser.getBasicProfile();
      console.log('ID: ' + profile.getId()); // Do not send to your backend! Use an ID token instead.
      console.log('Name: ' + profile.getName());
      console.log('Image URL: ' + profile.getImageUrl());
      console.log('Email: ' + profile.getEmail()); // This is null if the 'email' scope is not present.
    }
  }
};
</script>
