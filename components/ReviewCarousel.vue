<template>
  <div class="review-carousel">
    <v-row align="center" class="green lighten-1 pa-4">
      <v-col cols="8">
        <v-carousel
          cycle
          interval="4000"
          height="100%"
          :show-arrows="false"
          :hide-delimiters="true"
        >
          <v-carousel-item v-for="(review, i) in reviews" :key="i">
            <v-row align="center">
              <v-col cols="3" offset="1">
                <v-list class="review-avatar">
                  <v-list-item>
                    <v-list-item-avatar size="86" class="elevation-4">
                      <v-img :src="review.data.author_image.url" />
                    </v-list-item-avatar>
                  </v-list-item>
                  <v-list-item>
                    <v-list-item-title>{{
                      $prismic.asText(review.data.author_name)
                    }}</v-list-item-title>
                  </v-list-item>
                </v-list>
              </v-col>
              <v-col cols="8">
                <prismic-rich-text
                  :field="review.data.review_text"
                  class="pt-4 pr-6 white--text"
                />
              </v-col>
            </v-row>
          </v-carousel-item>
        </v-carousel>
      </v-col>
      <v-col cols="4" class="reviews-google">
        <v-row justify="center">
          <v-icon x-large color="yellow" class="mx-2"> mdi-star </v-icon>
          <v-icon x-large color="yellow" class="mx-2"> mdi-star </v-icon>
          <v-icon x-large color="yellow" class="mx-2"> mdi-star </v-icon>
          <v-icon x-large color="yellow" class="mx-2"> mdi-star </v-icon>
          <v-icon x-large color="yellow" class="mx-2"> mdi-star </v-icon>
        </v-row>
        <v-divider class="white mx-8"></v-divider>
        <h2>5</h2>
        <p>Google Reviews</p>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  props: {
    reviews: {
      type: Array,
      default() {
        return []
      },
    },
  },
}
</script>

<style lang="scss">
.review-carousel {
  p {
    font-size: 1.2rem;
    font-weight: 400;
  }
  .review-avatar {
    background-color: transparent !important;

    .v-list-item {
      justify-content: center;
    }
    .v-list-item__avatar {
      border: 2px solid #ffffff;
    }
    .v-list-item__title {
      font-size: 1.4rem;
      font-weight: bold;
      justify-content: center;
      display: inline-flex;
      padding-right: 1rem;
    }
  }
  .reviews-google {
    text-align: center;
    color: white;
    font-weight: bold;

    h2 {
      font-size: 3rem;
      line-height: 1 !important;
      padding-top: 1rem;
    }
  }
}
</style>
