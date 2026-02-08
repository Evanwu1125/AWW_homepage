<script setup>
const baseUrl = import.meta.env.BASE_URL
</script>

<template>
  <div>
    <el-divider />

    <el-row justify="center">
      <h1 class="section-title">Overview</h1>
    </el-row>

    <el-row justify="center">
      <el-col :xs="24" :sm="22" :md="20" :lg="18" :xl="16">
        <el-container class="image-container">
          <el-image
            class="overview-image"
            :src="`${baseUrl}main_figure.png`"
            fit="contain"
          />
        </el-container>
      </el-col>
    </el-row>
  </div>
</template>

<style scoped>
.image-container {
  margin: 20px 0 0 0;
}

.overview-image {
  width: 100%;
  border-radius: 12px;
  box-shadow: 0 10px 30px rgba(15, 23, 42, 0.08);
}
</style>
