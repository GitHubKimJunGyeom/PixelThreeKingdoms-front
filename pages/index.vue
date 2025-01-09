<template>
  <div class="fullscreen" @click="handleClick">
    <v-container class="fill-height d-flex align-center justify-center">
      <v-row>
        <v-col class="d-flex justify-center">
          <video 
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
      console.log("Click Position:", event.clientX, event.clientY);
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
