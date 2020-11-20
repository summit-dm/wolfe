<template>
  <v-row class="portfolio-preview blue-grey lighten-1">
    <v-container class="pa-2">
      <v-item-group>
        <v-row>
          <v-col v-for="(img, i) in portfolioContent.rowOne" :key="i" cols="4">
            <v-item>
              <v-img
                :src="img.url"
                height="220"
                class="rounded-lg border-accent"
                gradient="to top left, rgba(100,115,201,.4), rgba(25,32,72,.8)"
              />
            </v-item>
          </v-col>
        </v-row>
        <v-row>
          <v-col v-for="(img, i) in portfolioContent.rowTwo" :key="i" cols="2">
            <v-item>
              <v-img
                :src="img.url"
                height="108"
                class="rounded-lg border-accent"
                gradient="to top left, rgba(100,115,201,.2), rgba(25,32,72,.4)"
              />
            </v-item>
          </v-col>
        </v-row>
        <v-row>
          <v-col
            v-for="(img, i) in portfolioContent.rowThree"
            :key="i"
            cols="4"
          >
            <v-item>
              <v-img
                :src="img.url"
                height="220"
                class="rounded-lg border-accent"
                gradient="to top left, rgba(100,115,201,.3), rgba(25,32,72,.7)"
              />
            </v-item>
          </v-col>
        </v-row>
      </v-item-group>
    </v-container>
  </v-row>
</template>

<script>
export default {
  data() {
    return {
      portfolioContent: {
        rowOne: [],
        rowTwo: [],
        rowThree: [],
      },
      rowOne: [
        { url: 'https://cdn.vuetifyjs.com/images/backgrounds/bg.jpg' },
        { url: 'https://cdn.vuetifyjs.com/images/backgrounds/md.jpg' },
        { url: 'https://cdn.vuetifyjs.com/images/backgrounds/bg.jpg' },
      ],
      rowTwo: [
        { url: 'https://cdn.vuetifyjs.com/images/backgrounds/bg.jpg' },
        { url: 'https://cdn.vuetifyjs.com/images/backgrounds/md.jpg' },
        { url: 'https://cdn.vuetifyjs.com/images/backgrounds/bg.jpg' },
        { url: 'https://cdn.vuetifyjs.com/images/backgrounds/bg.jpg' },
        { url: 'https://cdn.vuetifyjs.com/images/backgrounds/md.jpg' },
        { url: 'https://cdn.vuetifyjs.com/images/backgrounds/bg.jpg' },
      ],
      rowThree: [
        { url: 'https://cdn.vuetifyjs.com/images/backgrounds/bg.jpg' },
        { url: 'https://cdn.vuetifyjs.com/images/backgrounds/md.jpg' },
        { url: 'https://cdn.vuetifyjs.com/images/backgrounds/bg.jpg' },
      ],
    }
  },
  created() {
    this.getContent()
    /* eslint-disable no-console */
  },
  methods: {
    getContent() {
      this.$prismic.api.getSingle('home_page').then((doc) => {
        const img1 = doc.data.image_1.url ? doc.data.image_1 : this.rowOne[0]
        const img2 = doc.data.image_2.url ? doc.data.image_2 : this.rowOne[1]
        const img3 = doc.data.image_3.url ? doc.data.image_3 : this.rowOne[2]
        const img4 = doc.data.image_4.url ? doc.data.image_4 : this.rowTwo[0]
        const img5 = doc.data.image_5.url ? doc.data.image_5 : this.rowTwo[1]
        const img6 = doc.data.image_6.url ? doc.data.image_6 : this.rowTwo[2]
        const img7 = doc.data.image_7.url ? doc.data.image_7 : this.rowTwo[3]
        const img8 = doc.data.image_8.url ? doc.data.image_8 : this.rowTwo[4]
        const img9 = doc.data.image_9.url ? doc.data.image_9 : this.rowTwo[5]
        const img10 = doc.data.image_10.url
          ? doc.data.image_10
          : this.rowThree[0]
        const img11 = doc.data.image_11.url
          ? doc.data.image_11
          : this.rowThree[1]
        const img12 = doc.data.image_12.url
          ? doc.data.image_12
          : this.rowThree[2]
        if (doc) {
          this.portfolioContent.rowOne = [img1, img2, img3]
          this.portfolioContent.rowTwo = [img4, img5, img6, img7, img8, img9]
          this.portfolioContent.rowThree = [img10, img11, img12]
        }
      })
    },
  },
}
</script>

<style lang="scss">
.portfolio-preview {
  .border-accent {
    border: 1px solid #607d8b;
    box-shadow: 0 0 0 1px #90a4ae;
  }
}
</style>
