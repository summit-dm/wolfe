<template>
  <div>
    <h1 class="hero-heading red--text text--darken-4">{{ title }}</h1>
    <p class="hero-subheading black--text">{{ subheading }}</p>
    <v-container v-for="(b, i) in buttons" :key="i" px-6>
      <v-btn
        v-if="i === 0"
        :to="$prismic.asLink(b.primary.button_link)"
        nuxt
        block
        elevation="6"
        rounded
        x-large
        class="white green--text mb-3"
      >
        {{ $prismic.asText(b.primary.button_label) }}
      </v-btn>
      <v-btn
        v-if="i === 1"
        :to="$prismic.asLink(b.primary.button_link)"
        nuxt
        block
        elevation="6"
        rounded
        x-large
        class="red darken-4 white--text my-3"
      >
        {{ $prismic.asText(b.primary.button_label) }}
      </v-btn>
      <v-btn
        v-if="i === 2"
        :to="$prismic.asLink(b.primary.button_link)"
        nuxt
        block
        elevation="6"
        rounded
        x-large
        class="blue darken-2 white--text my-3"
      >
        {{ $prismic.asText(b.primary.button_label) }}
      </v-btn>
    </v-container>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      default: 'Title',
    },
    subheading: {
      type: String,
      default: 'Subheading paragraph',
    },
    buttons: {
      type: Array,
      default() {
        return []
      },
    },
  },
}
</script>

<style lang="scss">
.hero-heading {
  font-size: 3rem;
  text-align: center;
  padding: 0.6rem 1rem;
  margin-top: 0;
}
.hero-subheading {
  padding: 0rem 2rem 2rem 2rem;
  font-size: 1.2rem;
  font-weight: 500;
}
</style>
