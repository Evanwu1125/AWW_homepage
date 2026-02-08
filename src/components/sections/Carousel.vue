<script>
export default {
  data() {
    return {
      row1Images: [
        '/front/1.png',
        '/front/2.png',
        '/front/3.png',
        '/front/4.png',
        '/front/5.png',
        '/front/6.png',
        '/front/7.png',
        '/front/8.png',
        '/front/9.png',
        '/front/10.png',
        '/front/11.png',
        '/front/12.png',
        '/front/13.png',
        '/front/14.png',
        '/front/15.png',
        '/front/16.png',
      ],
      row2Images: [
        '/front/17.png',
        '/front/18.png',
        '/front/19.png',
        '/front/20.png',
        '/front/21.png',
        '/front/22.png',
        '/front/23.png',
        '/front/24.png',
        '/front/25.png',
        '/front/26.png',
        '/front/27.png',
        '/front/28.png',
        '/front/29.png',
        '/front/30.png',
        '/front/31.png',
        '/front/32.png',
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
