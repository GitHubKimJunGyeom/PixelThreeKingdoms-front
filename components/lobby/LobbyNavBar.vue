<template>
    <v-app>
      <v-main>
        <v-container>
          <!-- Your main content here -->
        </v-container>
        
        <!-- Bottom Navigation Bar -->
        <v-bottom-navigation
          app
          fixed
          color="primary"
          active-color="white"
          dark
        >
          <v-btn
            value="character"
            @click="onNavigate('character')"
          >
            <v-icon>mdi-account</v-icon>
            Character 
          </v-btn>
  
          <v-btn
            value="stage"
            @click="onNavigate('stage')"
          >
            <v-icon>mdi-map</v-icon>
            Stage
          </v-btn>
  
          <v-btn
            value="gacha"
            @click="onNavigate('gacha')"
          >
            <v-icon>mdi-dice-multiple</v-icon>
            gachar
          </v-btn>
  
          <v-btn
            value="options"
            @click="onNavigate('options')"
          >
            <v-icon>mdi-cog</v-icon>
            option
          </v-btn>
        </v-bottom-navigation>
      </v-main>
    </v-app>
  </template>
  
  <script>
  export default {
    methods: {
      onNavigate(page) {
        console.log(`${page} 페이지로 이동합니다.`);
        // 페이지 이동 로직 추가
      },
    },
  };
  </script>
  
  <style>
  /* 추가적인 스타일링이 필요하면 여기에 작성하세요 */
  </style>
  