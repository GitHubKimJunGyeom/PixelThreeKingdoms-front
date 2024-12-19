<template>
  <div class="fullscreen" @click="handleClick">
    <v-container class="fill-height d-flex align-center justify-center">
      <v-row>
        <v-col class="d-flex justify-center">
          <video 
            src="temp.mp4" 
            controls 
            autoplay 
            loop 
            class="video-player">
          </video>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  methods: {
    handleClick(event) {
      console.log("클릭 위치:", event.clientX, event.clientY);
      // 원하는 로직 추가
    },
  },
};
</script>

<style scoped>
.fullscreen {
  background-color: black;
  width: 100vw;
  height: 100vh;
  overflow: hidden;
  position: relative;
}

.video-player {
  max-width: 100%;
  max-height: 100%;
  display: block;
  border: none;
}
</style>
