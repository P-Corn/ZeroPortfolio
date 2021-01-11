<template>
<div class="projects-container">
  <!-- v-if Desktop show -->
  <v-slide-group
    v-if="windowWidth > 600"
    :key="String(reset)"
    v-intersect.once="onObserve"
    v-bind="$attrs"
    v-on="$listeners"
  >
    <v-slide-item
      v-for="(card, i) in filtered"
      :key="i"
      v-slot:default="{ active, toggle }"
    >
      <div>
        <project-card
          :active="active"
          :height="height"
          :src="require(`@/assets/project-${i + 1}.jpg`)"
          :width="width"
          v-bind="card"
          class="mx-3"
          @click="toggle"
        />
      </div>
    </v-slide-item>
  </v-slide-group>

  <!-- v-if mobile then show -->
  <v-carousel v-model="model" 
    v-if="windowWidth <= 600"
    :show-arrows="true"
    hide-delimiters
  >
    <v-carousel-item
      v-for="(card, i) in filtered"
      :key="i"
    >
      <v-sheet
        height="100%"
        tile
        color="#fafafa"
      >
        <v-row
          class="fill-height"
          align="center"
          justify="center"
        >
          <project-card
          height="400"
          :src="require(`@/assets/project-${i + 1}.jpg`)"
          v-bind="card"
          class="mx-3 projectCard"
        />

        </v-row>
      </v-sheet>
    </v-carousel-item>
  </v-carousel>
  
</div>
</template>

<script>
  export default {
    name: 'SectionProjects',

    components: {
      ProjectCard: () => import('@/components/ProjectCard'),
    },

    props: {
      filter: {
        type: Function,
        default: v => !!v,
      },
      height: {
        type: [Number, String],
        default: 125,
      },
      width: {
        type: [Number, String],
        default: 175,
      },
    },

    data: () => ({
      cards: [
        { title: 'Cierra Vega', subtitle: 'Wordpress' },
        { title: 'Pierre Cox', subtitle: 'Statistics' },
        { title: 'Alden Cantrell', subtitle: 'Wordpress' },
        { title: 'Kierra Gentry', subtitle: 'Branding' },
        { title: 'Thomas Crane', subtitle: 'Shopping' },
        { title: 'Miranda Shaffer', subtitle: 'Branding' },
        { title: 'Bradyn Kramer', subtitle: 'Photography' },
        { title: 'Bailey Wolfe', subtitle: 'Wordpress' },
      ],
      reset: false,
      windowWidth: window.innerWidth,
      mobile: null,
      model: 0,
    }),

    computed: {
      filtered () {
        return this.cards.filter(this.filter)
      },
    },
    
    created() {
      window.addEventListener("resize", this.windowSize);
    },

    destroyed() {
      window.removeEventListener("resize", this.windowSize);
    },

    methods: {
      windowSize() {
          this.windowWidth = window.innerWidth
      },
      onObserve (x, y, isVisible) {
        if (this.reset) return

        // Workaround for now
        // Issue lies within the slide-group's
        // logic to re-calculate the container's
        // overflow
        setTimeout(() => {
          this.reset = !this.reset
        }, 100)
      },
    },
  }
</script>

<style lang='scss'>
.projects-container{
  width: 100%;
}

.projectCard {
  width: 100%;
  h3 {
    color: green;
  }
}
</style>