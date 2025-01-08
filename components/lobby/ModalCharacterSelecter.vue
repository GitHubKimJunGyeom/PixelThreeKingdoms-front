<template>
    <v-container>
      <v-carousel 
        show-arrows
        cycle
        height="400px"
      >
        <!-- 슬라이드 1 -->
        <v-carousel-item>
          <v-img src="https://via.placeholder.com/800x400?text=Slide+1" />
        </v-carousel-item>
  
        <!-- 슬라이드 2 -->
        <v-carousel-item>
          <v-img src="https://via.placeholder.com/800x400?text=Slide+2" />
        </v-carousel-item>
  
        <!-- 슬라이드 3 -->
        <v-carousel-item>
          <v-img src="https://via.placeholder.com/800x400?text=Slide+3" />
        </v-carousel-item>
      </v-carousel>
    </v-container>
  </template>
  
  <script>
  export default {
    name: "CustomCarousel",
  };
  </script>
  
  <style>
  /* 필요하면 스타일을 추가하세요 */
  </style>
  