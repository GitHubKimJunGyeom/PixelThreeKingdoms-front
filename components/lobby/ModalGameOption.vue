<template>
    <div class="audio-control">
      <div class="audio-control-item">
        <!-- 음량 조절 프로그레스바 -->
        <label for="volume-slider">Volume</label>
        <input
          type="range"
          id="volume-slider"
          v-model="volume"
          min="0"
          max="100"
          step="1"
          @input="updateVolume"
          class="volume-slider"
        />
        <span>{{ volume }}%</span>
      </div>
  
      <div class="audio-control-item">
        <!-- 음량 온오프 체크박스 -->
        <label for="mute-checkbox">Volume off</label>
        <input
          type="checkbox"
          id="mute-checkbox"
          v-model="isMuted"
          @change="toggleMute"
          class="mute-checkbox"
        />
      </div>
  
      <div class="audio-control-item">
        <!-- 배경음악 종류 선택 라디오 버튼 -->
        <label>BGM</label>
        <div>
          <input
            type="radio"
            id="music1"
            value="music1"
            v-model="selectedMusic"
            @change="changeMusic"
          />
          <label for="music1">BGM1</label>
        </div>
        <div>
          <input
            type="radio"
            id="music2"
            value="music2"
            v-model="selectedMusic"
            @change="changeMusic"
          />
          <label for="music2">BGM2</label>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        volume: 50, // 초기 음량
        isMuted: false, // 음량 상태 (켜짐/꺼짐)
        selectedMusic: "music1", // 선택된 배경음악
      };
    },
    methods: {
      updateVolume() {
        if (this.isMuted) {
          this.isMuted = false;
        }
        this.$refs.audioPlayer.volume = this.volume / 100;
      },
      toggleMute() {
        if (this.isMuted) {
          this.volume = 0;
        } else {
          this.volume = 50;
        }
        this.$refs.audioPlayer.volume = this.isMuted ? 0 : this.volume / 100;
      },
      changeMusic() {
        const audioPlayer = this.$refs.audioPlayer;
        if (this.selectedMusic === "music1") {
          audioPlayer.src = "path/to/music1.mp3"; // 음악 1 경로
        } else {
          audioPlayer.src = "path/to/music2.mp3"; // 음악 2 경로
        }
        audioPlayer.play();
      },
    },
    mounted() {
      // 오디오 요소를 초기화합니다.
      this.$refs.audioPlayer.src = "path/to/music1.mp3"; // 기본 음악
      this.$refs.audioPlayer.volume = this.volume / 100;
    },
  };
  </script>
  
  <style scoped>
  .audio-control {
    display: flex;
    flex-direction: column;
    gap: 16px;
  }
  
  .audio-control-item {
    display: flex;
    align-items: center;
    gap: 8px;
  }
  
  .volume-slider {
    width: 200px;
  }
  
  .mute-checkbox {
    transform: scale(1.2);
  }
  </style>
  
  <!-- 배경음악을 위한 오디오 태그 -->
  <audio ref="audioPlayer" loop></audio>
  