<script lang="ts" setup>
import { h, ref } from 'vue'
import { ElIcon } from 'element-plus'
import { Document, Files, DataAnalysis } from '@element-plus/icons-vue'

// Hugging Face emoji icon for Model button
const HfIcon = {
  render() {
    return h('span', { style: 'font-size: 18px; font-style: normal;' }, '🤗')
  },
}

// Base URL for assets
const baseUrl = import.meta.env.BASE_URL

// Logo path (set to '' to hide)
const logo = `${baseUrl}logo.png`

// Title configuration
const titleMain = 'AutoWebWorld'
const titleRest =
  ": Synthesizing Infinite Verifiable Web Environments via Finite State Machines"
const titleColor = '#000000'
const titleSupp = ''
const titleSuppColor = '#42B883'

// Button color
const btnColor = '#444444'

// Authors (name, homepage, affiliation flags)
const authors = [
  {
    name: 'Yifan Wu',
    icon: '',
    homepage: '',
    addressFlag: '1,2',
  },
  {
    name: 'Yiran Peng',
    icon: '',
    homepage: '',
    addressFlag: '2',
  },
  {
    name: 'Yiyu Chen',
    icon: '',
    homepage: '',
    addressFlag: '1',
  },
  { name: 'Jianhao Ruan', icon: '', homepage: '', addressFlag: '1,2' },
  { name: 'Cheng Yang', icon: '', homepage: '', addressFlag: '2' },
  { name: 'Jiayi Zhang', icon: '', homepage: '', addressFlag: '1,2' },
  {
    name: 'Man Chen',
    icon: '',
    homepage: '',
    addressFlag: '1',
  },
  { name: 'Yenchi Tseng', icon: '', homepage: '', addressFlag: '1' },
  {
    name: 'Zhaoyang Yu',
    icon: '',
    homepage: '',
    addressFlag: '2',
  },
  { name: 'Liang Chen', icon: '', homepage: '', addressFlag: '3' },
  {
    name: 'Yuyao Zhai',
    icon: '',
    homepage: '',
    addressFlag: '3',
  },
    {
    name: 'Bang Liu',
    icon: '',
    homepage: '',
    addressFlag: '4†',
  },
  {
    name: 'Chenglin Wu',
    icon: '',
    homepage: '',
    addressFlag: '2\u2020',
  },
  {
    name: 'Yuyu Luo',
    icon: '',
    homepage: '',
    addressFlag: '1\u2020',
  },
]

// Affiliations
const addresses = [
  { addressFlag: '1', name: 'Hong Kong University of Science and Technology (GuangZhou)', icon: '', homepage: '' },
  { addressFlag: '2', name: 'DeepWisdom', icon: '', homepage: '' },
  { addressFlag: '3', name: 'Peking University', icon: '', homepage: '' },
  { addressFlag: '4', name: 'Université de Montréal \& Mila', icon: '', homepage: '' },
]

// Author note
const conAndCorresponding =
  '\u2020 Corresponding Author.'

// Emphasis lines (empty for now, no extra block)
const emphases: string[] = []

// Resource buttons
const buttons = [
  { disabled: false, name: 'Paper', link: 'https://arxiv.org/abs/2511.15065', component: Document },
  {
    disabled: false,
    name: 'Code',
    link: 'https://github.com/Evanwu1125/AutoWebWorld',
    component: Files,
  },
  // {
  //   disabled: false,
  //   name: 'Dataset',
  //   link: 'https://huggingface.co/datasets/amagipeng/VR-Bench',
  //   component: DataAnalysis,
  // },
  // {
  //   disabled: false,
  //   name: 'Model',
  //   link: 'https://huggingface.co/HY-Wan/Wan-R1',
  //   component: HfIcon,
  // },
]

const showDetails = ref(false)

const toggleDetails = () => {
  showDetails.value = !showDetails.value
}
</script>

<template>
  <div>
    <!-- Logo -->
    <el-row v-if="logo" justify="center" style="margin-top: 20px">
      <el-image :src="logo" class="logo" fit="contain" />
    </el-row>

    <!-- Title -->
    <el-row justify="center">
      <el-col :span="20">
        <h1 class="paper-title">
          <span v-if="titleMain" class="title-gradient">{{ titleMain }}</span>
          <span v-if="titleRest" :style="{ color: titleColor }"> {{ titleRest }}</span>
          <span v-if="titleSupp" :style="{ color: titleSuppColor }"> {{ titleSupp }}</span>
        </h1>
      </el-col>
    </el-row>

    <el-row justify="center" class="anonymity-controls">
      <el-button class="anonymity-button" type="primary" plain @click="toggleDetails">
        {{ showDetails ? 'Hide author info' : 'Reveal author info' }}
      </el-button>
    </el-row>

    <div class="author-section">
      <transition name="fade-switch" mode="out-in">
      <div v-if="showDetails" key="details" class="details-panel">
        <!-- Authors -->
        <el-row justify="center">
          <a
            v-for="author in authors"
            :key="author.name"
            :href="author.homepage || 'javascript:void(0);'"
          >
            <el-button class="title-button" type="primary" text>
              <el-avatar
                v-if="author.icon"
                :size="40"
                :src="author.icon"
                class="author-avatar"
              />
              <span class="author">
                {{ author.name
                }}<sup v-if="author.addressFlag" class="name_sup">{{ author.addressFlag }}</sup>
              </span>
            </el-button>
          </a>
        </el-row>

        <!-- Affiliations -->
        <el-row justify="center">
          <a
            v-for="address in addresses"
            :key="address.name"
            :href="address.homepage || 'javascript:void(0);'"
          >
            <el-button class="title-button" type="primary" text>
              <span class="address">
                <sup v-if="address.addressFlag" class="address_sup">{{ address.addressFlag }}</sup>
                {{ address.name }}
              </span>
            </el-button>
          </a>
        </el-row>

        <!-- Equal contribution / corresponding note -->
        <el-row v-if="conAndCorresponding" justify="center" class="con-cor">
          <span class="con-cor-text">{{ conAndCorresponding }}</span>
        </el-row>
        <el-row justify="center" class="con-cor-logo">
          <el-image :src="`${baseUrl}foundation_agent.png`" class="con-logo" fit="contain" />
        </el-row>
      </div>
      <div v-else key="mask">
        <div class="mask-panel">
          <p>Author and affiliation details are anonymized.</p>
          <p>Click “Reveal author info” to make them visible.</p>
        </div>
      </div>
      </transition>
    </div>

    <!-- Emphasis block (currently empty) -->
    <el-row
      v-for="emphasis in emphases"
      :key="emphasis"
      justify="center"
      class="emphasis"
    >
      {{ emphasis }}
    </el-row>

    <!-- Resource buttons -->
    <el-row justify="center" style="margin-bottom: 20px">
      <el-col :span="20">
        <el-row justify="center">
          <a
            v-for="button in buttons"
            :key="button.name"
            :href="button.link || 'javascript:void(0);'"
          >
            <el-button
              class="guidance-button"
              size="default"
              :color="btnColor"
              :disabled="button.disabled"
              round
            >
              <el-icon :size="18">
                <component :is="button.component" />
              </el-icon>
              <span class="btn-text">{{ button.name }}</span>
            </el-button>
          </a>
        </el-row>
      </el-col>
    </el-row>
  </div>
</template>

<style scoped>
/* Title font and layout */
.paper-title {
  font-family: 'Droid Serif', 'Times New Roman', serif;
  letter-spacing: 2px;
  font-size: 42px;
  margin: 32px;
  text-align: center;
}

/* VR-Bench gradient text */
.title-gradient {
  background: linear-gradient(90deg, #2f88ff 0%, #6c42ff 100%);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}

/* Author and affiliation buttons */
.title-button {
  margin: 10px 3px;
}

.title-button:hover {
  margin: 10px 8px;
}

.anonymity-controls {
  margin-top: 10px;
}

.anonymity-button {
  min-width: 220px;
  height: 46px;
  font-size: 16px;
  font-weight: 600;
  font-family: 'Droid Serif', 'Times New Roman', serif;
  border-radius: 24px;
  background: #5a5a5a;
  border-color: #5a5a5a;
}

.anonymity-button:hover {
  background: #6f6f6f;
  border-color: #6f6f6f;
}

.anonymity-button.is-plain {
  color: #ffffff;
}

.author-section {
  position: relative;
  margin-top: 10px;
}

.mask-panel {
  background: #d3d3d3;
  border-radius: 12px;
  padding: 24px;
  text-align: center;
  font-family: 'Droid Serif', 'Times New Roman', serif;
  color: #606266;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
}

.fade-switch-enter-active,
.fade-switch-leave-active {
  transition: opacity 0.35s ease, filter 0.35s ease;
}

.fade-switch-enter-from,
.fade-switch-leave-to {
  opacity: 0;
  filter: blur(2px);
}

/* Resource buttons */
.guidance-button {
  margin: 8px 5px;
  box-shadow: #d8d8d8 1px 1px 1px 1px;
}

/* Author text: bolder and more prominent */
.author {
  font-family: 'Droid Serif', 'Times New Roman', serif;
  font-size: 20px;
  font-weight: 600;
  margin-left: 3px;
}

/* Superscript for authors */
.name_sup {
  font-family: 'Droid Serif', 'Times New Roman', serif;
  color: #606266;
  margin-left: 3px;
}

/* Affiliation text: different, lighter font */
.address {
  font-family: 'Droid Serif', 'Times New Roman', serif;
  font-size: 16px;
  font-weight: 400;
}

/* Superscript for affiliations */
.address_sup {
  color: #606266;
  margin-right: 1px;
}

/* Contribution note */
.con-cor {
  font-family: 'Droid Serif', 'Times New Roman', serif;
  font-size: 14px;
  margin: 18px 0;
  text-align: center;
}

.con-cor-text {
  font-style: italic;
}

.con-cor-logo {
  margin-bottom: 10px;
}

.con-logo {
  max-width: 360px;
  width: 80%;
}

/* Emphasis lines */
.emphasis {
  color: chocolate;
  font-weight: bold;
  margin: 8px;
  font-size: 22px;
  text-align: center;
}

/* Resource button text */
.btn-text {
  font-size: 18px;
  color: #ffffff;
}

/* Logo display */
.logo {
  max-width: 200px;
  width: auto;
  height: auto;
  margin-top: 40px;
}

/* Link styles */
a:-webkit-any-link {
  text-decoration: none;
}

a:hover {
  color: inherit;
  border-bottom: none;
}

a {
  text-decoration: none;
  color: inherit;
}
</style>
