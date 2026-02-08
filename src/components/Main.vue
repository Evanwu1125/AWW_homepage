<script>
import Title from './sections/Title.vue'
import Abstract from './sections/Abstract.vue'
import BibTeX from './sections/BibTeX.vue'
import Carousel from './sections/Carousel.vue'
import Overview from './sections/Overview.vue'
import CaseDemonstration from './sections/CaseDemonstration.vue'

export default {
  components: {
    Title,
    Abstract,
    BibTeX,
    Carousel,
    Overview,
    CaseDemonstration
  }
}
</script>

<template>
  <Title/>
  <Carousel/>
  <Overview/>
  <Abstract/>
  <CaseDemonstration/>
  <BibTeX/>
</template>
