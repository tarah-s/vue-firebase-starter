<template>
  <div class="hero is-light is-fullheight-with-navbar">
    <div class="hero-body">
      <div class="container">
          <div id="firebaseui-auth-container"></div>
      </div>
    </div>
  </div>
</template>

<script>
import firebase from "@/firebaseinit";
import "firebaseui";
import "firebaseui/dist/firebaseui.css";

const ui = new firebaseui.auth.AuthUI(firebase.auth());

export default {
  mounted() {
    this.showSignInUi();
  },
  methods: {
    showSignInUi() {
      const uiConfig = {
        signInSuccessUrl: "/profile",
        signInOptions: [
          firebase.auth.GoogleAuthProvider.PROVIDER_ID,
          firebase.auth.EmailAuthProvider.PROVIDER_ID
        ]
      };
      ui.start("#firebaseui-auth-container", uiConfig);
    }
  }
};
</script>