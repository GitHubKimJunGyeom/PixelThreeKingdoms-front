<template>
    <v-container>
      <!-- Header Section -->
      <v-row>
        <v-col>
          <v-card outlined>
            <v-card-title>Character Status</v-card-title>
            <v-card-text>
              <div>Attack: {{ status.attack }}</div>
              <div>Defense: {{ status.defense }}</div>
              <div>Health: {{ status.health }}</div>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
  
      <!-- Main Section -->
      <v-row class="mt-4">
        <v-col>
          <v-card outlined>
            <v-img :src="characterImage" alt="Character" aspect-ratio="1"></v-img>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </template>
  
  <script>
  export default {
    data() {
      return {
        status: {
          attack: 0,
          defense: 0,
          health: 0,
        },
        characterImage: "https://via.placeholder.com/300", // 기본 이미지 URL
      };
    },
    mounted() {
      this.fetchStatus();
    },
    methods: {
      async fetchStatus() {
        try {
          // 서버에서 상태 정보를 가져오는 API 요청
          const response = await fetch("/api/character/status");
          const data = await response.json();
          this.status = {
            attack: data.attack,
            defense: data.defense,
            health: data.health,
          };
        } catch (error) {
          console.error("Failed to fetch status", error);
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .mt-4 {
    margin-top: 16px;
  }
  </style>
  