<script>
  // Extensions
  import View from '@/views/View'

  // Mixins
  import LoadSections from '@/mixins/load-sections'

  export default {
    name: 'Article',

    metaInfo: { title: 'News Single' },

    extends: View,

    mixins: [
      LoadSections([
        'hero-alt',
        'article',
        'social-media',
        'news',
        'newsletter-alt',
        'info',
      ]),
    ],

    props: {
      id: {
        type: String,
        default: 'article',
      },
    },
  }
</script>
