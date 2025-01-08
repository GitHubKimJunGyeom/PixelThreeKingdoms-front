<template>
    <v-app>
      <!-- 상단 네비게이션 바 -->
      <v-app-bar app>
        <v-toolbar-title>픽셀 삼국</v-toolbar-title>
        <v-spacer></v-spacer>
        <v-btn text>홈</v-btn>
        <v-btn text>게임</v-btn>
        <v-btn text>설정</v-btn>
      </v-app-bar>
  
      <!-- 네비게이션 바에 의해 전환되는 화면 -->
      <v-main>
        <v-container fluid>
          <v-row>
            <v-col cols="12" md="3">
              <!-- 세로 버튼 리스트 -->
              <v-btn v-for="(button, index) in verticalButtons" :key="index" block>
                {{ button }}
              </v-btn>
            </v-col>
            <v-col cols="12" md="9">
              <!-- 메인 콘텐츠 영역 (예시로 텍스트 추가) -->
              <v-card>
                <v-card-title>메인 화면</v-card-title>
                <v-card-text>
                  화면 전환이 가능합니다.
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </v-main>
    </v-app>
  </template>
  
  <script>
  export default {
    data() {
      return {
        verticalButtons: ['버튼 1', '버튼 2', '버튼 3', '버튼 4']
      };
    }
  };
  </script>
  
  <style scoped>
  .v-app-bar {
    background-color: #000000; /* 검정색 배경 */
  }
  
  .v-btn {
    color: white; /* 버튼 텍스트 색상 */
  }
  </style>
  