<template>
  <v-theme-provider dark>
    <base-section
      id="social"
      class="accent text-center"
      space="8"
    >
      <base-icon class="mb-8 mt-4">
        mdi-twitter
      </base-icon>
      <base-icon class="ml-3 mb-8 mt-4">
        mdi-instagram
      </base-icon>

      <base-section-heading
        color="transparent"
        title="Social Media"
      >
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Excepturi aspernatur recusandae aut repudiandae illo error obcaecati dolores voluptate, tempore.
      </base-section-heading>

      <v-btn
        class="font-weight-bold mx-5 mb-4"
        color="white"
        href="https://twitter.com/vuetifyjs"
        light
        min-width="168"
        target="_blank"
        x-large
      >
        twitter

        <v-icon right>
          mdi-open-in-new
        </v-icon>
      </v-btn>

      <v-btn
        class="font-weight-bold mx-5 mb-4"
        color="white"
        href="https://twitter.com/vuetifyjs"
        light
        min-width="168"
        target="_blank"
        x-large
      >
        Instagram
        <v-icon right>
          mdi-open-in-new
        </v-icon>
      </v-btn>
    </base-section>
  </v-theme-provider>
</template>

<script>
  export default {
    name: 'SectionNews',

    provide: {
      heading: { align: 'center' },
    },
  }
</script>
