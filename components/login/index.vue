<template>
    <v-app>
      <v-container>
        <v-row justify="center">
          <v-col cols="12" sm="8" md="6">
            <v-card class="elevation-12">
              <v-toolbar color="primary" dark flat>
                <v-toolbar-title>로그인</v-toolbar-title>
              </v-toolbar>
  
              <v-card-text>
                <div id="GgCustomLogin" class="text-center">
                  <v-btn color="red" dark @click="onGoogleLogin">
                    <v-icon left>mdi-google</v-icon>
                    Google로 로그인하기
                  </v-btn>
                </div>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-app>
  </template>
  
  <script>
  export default {
    head() {
      return {
        script: [
          {
            src: 'https://apis.google.com/js/platform.js',
            async: true,
            defer: true
          }
        ]
      }
    },
    mounted() {
      this.initGoogleAuth();
    },
    methods: {
      initGoogleAuth() {
        gapi.load("auth2", () => {
          const auth2 = gapi.auth2.init({
            client_id: "217755353555-3msma49ckq4fa47k0tg5tkshatcdh8c9.apps.googleusercontent.com",
            scope: "email profile openid https://www.googleapis.com/auth/user.birthday.read",
          });
          this.authInstance = auth2;
        });
      },
      onGoogleLogin() {
        if (!this.authInstance) {
          console.error("Google Auth Instance not initialized.");
          return;
        }
        this.authInstance.signIn().then(
          (googleUser) => {
            const accessToken = googleUser.getAuthResponse().access_token;
            const profile = googleUser.getBasicProfile();
            console.log("User Profile:", profile);
  
            // Google People API 요청
            this.$axios
              .$get("https://people.googleapis.com/v1/people/me", {
                params: {
                  personFields: "birthdays",
                  key: "AIzaSyBOdmeC4SOSzXmPGLEM2vZueqiBSWKg3wk",
                  access_token: accessToken,
                },
              })
              .then((response) => {
                console.log("People API Response:", response);
              })
              .catch((error) => {
                console.error("People API Error:", error);
              });
          },
          (error) => {
            console.error("Google Sign-In Error:", error);
          }
        );
      },
    },
  };
  </script>
  
  <style>
  #GgCustomLogin {
    margin-top: 20px;
  }
  </style>