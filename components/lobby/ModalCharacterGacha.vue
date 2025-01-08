<template>
    <v-container class="infinite-grid" fluid>
      <v-row dense>
        <v-col
          v-for="(item, index) in visibleItems"
          :key="index"
          cols="1"
          md="1"
          class="grid-item"
        >
          {{ item }}
        </v-col>
      </v-row>
      <div ref="scrollTarget" class="scroll-target"></div>
    </v-container>
  </template>
  
  <script>
  export default {
    data() {
      return {
        gridData: Array.from({ length: 1000 }, (_, i) => `Item ${i + 1}`),
        visibleItems: [],
        batchSize: 50, // 한 번에 로드할 항목 수
      };
    },
    mounted() {
      this.loadMore();
      const observer = new IntersectionObserver(
        (entries) => {
          if (entries[0].isIntersecting) {
            this.loadMore();
          }
        },
        { root: null, rootMargin: "0px", threshold: 1.0 }
      );
      observer.observe(this.$refs.scrollTarget);
    },
    methods: {
      loadMore() {
        const nextBatch = this.gridData.splice(0, this.batchSize);
        this.visibleItems.push(...nextBatch);
      },
    },
  };
  </script>
  
  <style scoped>
  .infinite-grid {
    max-width: 100%;
    overflow-x: hidden;
  }
  .grid-item {
    text-align: center;
    padding: 16px;
    background-color: #f5f5f5;
    border: 1px solid #ddd;
    height: 100px; /* 원하는 높이로 조정 가능 */
  }
  .scroll-target {
    height: 1px;
  }
  </style>
  