<script>
export default {
  data() {
    const baseUrl = import.meta.env.BASE_URL
    return {
      row1Images: [
        `${baseUrl}front/1.png`,
        `${baseUrl}front/2.png`,
        `${baseUrl}front/3.png`,
        `${baseUrl}front/4.png`,
        `${baseUrl}front/5.png`,
        `${baseUrl}front/6.png`,
        `${baseUrl}front/7.png`,
        `${baseUrl}front/8.png`,
        `${baseUrl}front/9.png`,
        `${baseUrl}front/10.png`,
        `${baseUrl}front/11.png`,
        `${baseUrl}front/12.png`,
        `${baseUrl}front/13.png`,
        `${baseUrl}front/14.png`,
        `${baseUrl}front/15.png`,
        `${baseUrl}front/16.png`,
      ],
      row2Images: [
        `${baseUrl}front/17.png`,
        `${baseUrl}front/18.png`,
        `${baseUrl}front/19.png`,
        `${baseUrl}front/20.png`,
        `${baseUrl}front/21.png`,
        `${baseUrl}front/22.png`,
        `${baseUrl}front/23.png`,
        `${baseUrl}front/24.png`,
        `${baseUrl}front/25.png`,
        `${baseUrl}front/26.png`,
        `${baseUrl}front/27.png`,
        `${baseUrl}front/28.png`,
        `${baseUrl}front/29.png`,
        `${baseUrl}front/30.png`,
        `${baseUrl}front/31.png`,
        `${baseUrl}front/32.png`,
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
