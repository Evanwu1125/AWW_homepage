<script>
export default {
  data() {
    return {
      row1Images: [
        '/VRBench_Web/front/1.png',
        '/VRBench_Web/front/2.png',
        '/VRBench_Web/front/3.png',
        '/VRBench_Web/front/4.png',
        '/VRBench_Web/front/5.png',
        '/VRBench_Web/front/6.png',
        '/VRBench_Web/front/7.png',
        '/VRBench_Web/front/8.png',
        '/VRBench_Web/front/9.png',
        '/VRBench_Web/front/10.png',
        '/VRBench_Web/front/11.png',
        '/VRBench_Web/front/12.png',
        '/VRBench_Web/front/13.png',
        '/VRBench_Web/front/14.png',
        '/VRBench_Web/front/15.png',
        '/VRBench_Web/front/16.png',
      ],
      row2Images: [
        '/VRBench_Web/front/17.png',
        '/VRBench_Web/front/18.png',
        '/VRBench_Web/front/19.png',
        '/VRBench_Web/front/20.png',
        '/VRBench_Web/front/21.png',
        '/VRBench_Web/front/22.png',
        '/VRBench_Web/front/23.png',
        '/VRBench_Web/front/24.png',
        '/VRBench_Web/front/25.png',
        '/VRBench_Web/front/26.png',
        '/VRBench_Web/front/27.png',
        '/VRBench_Web/front/28.png',
        '/VRBench_Web/front/29.png',
        '/VRBench_Web/front/30.png',
        '/VRBench_Web/front/31.png',
        '/VRBench_Web/front/32.png',
      ],
    }
  },
}
</script>

<template>
  <div class="carousel-wrapper">
    <el-row justify="center">
      <el-col :span="24">
        <div class="carousel-row row-1">
          <div class="carousel-track track-left">
            <el-image
              v-for="path in row1Images"
              :key="`r1-${path}`"
              :src="path"
              fit="contain"
              class="carousel-image"
            />
            <!-- duplicate for seamless effect -->
            <el-image
              v-for="path in row1Images"
              :key="`r1b-${path}`"
              :src="path"
              fit="contain"
              class="carousel-image"
            />
          </div>
        </div>
      </el-col>
    </el-row>

    <el-row justify="center">
      <el-col :span="24">
        <div class="carousel-row row-2">
          <div class="carousel-track track-right">
            <el-image
              v-for="path in row2Images"
              :key="`r2-${path}`"
              :src="path"
              fit="contain"
              class="carousel-image"
            />
            <!-- duplicate for seamless effect -->
            <el-image
              v-for="path in row2Images"
              :key="`r2b-${path}`"
              :src="path"
              fit="contain"
              class="carousel-image"
            />
          </div>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<style scoped>
.carousel-wrapper {
  margin-top: 10px;
  font-family: 'Times New Roman', 'Times', serif;
}

.carousel-row {
  overflow: hidden;
  white-space: nowrap;
  margin: 10px 0;
}

.carousel-row:hover .carousel-track {
  animation-play-state: paused;
}

.carousel-track {
  display: inline-flex;
}

.carousel-image {
  width: 480px;
  height: 270px;
  margin: 0 8px;
  border-radius: 10px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.12);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  transform-origin: center center;
  will-change: transform;
}

.carousel-image:hover {
  transform: scale(1.08);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.18);
  z-index: 1;
}
.track-left {
  animation: scroll-left 45s linear infinite;
}

.track-right {
  animation: scroll-right 45s linear infinite;
}

@keyframes scroll-left {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(-50%);
  }
}

@keyframes scroll-right {
  0% {
    transform: translateX(-50%);
  }
  100% {
    transform: translateX(0);
  }
}
</style>
