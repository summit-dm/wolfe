<template>
  <div>
    <v-row
      justify="center"
      align="center"
      class="hero-container"
      :style="bgrdStyle"
    >
      <v-col cols="12" sm="8" md="6">
        <!-- <hero
          :title="heroTitle"
          :subheading="heroSubHead"
          :buttons="heroButtons"
        /> -->
      </v-col>
    </v-row>
    <!-- <review-carousel :reviews="reviews" />
    <portfolio-preview />
    <process /> -->
    <cta-triple />
    <cta-double />
  </div>
</template>

<script>
import { groq } from '@nuxtjs/sanity'

const query = groq`*[]`

export default {
  /* eslint-disable no-console */
  async fetch() {
    const result = await this.$sanity.fetch(query)
    this.doc = result
    console.log(this.doc[0].title)
  },
  data() {
    return {
      doc: {},
      bgrdStyle: 'background: #ffffff;',
    }
  },
}
</script>

<style lang="scss">
.hero-container {
  padding-bottom: 2rem;
  box-shadow: 0px 8px 16px -8px rgba($color: #000000, $alpha: 0.4);
  z-index: 1;
  position: relative;
  padding-top: 156px;
}
</style>
