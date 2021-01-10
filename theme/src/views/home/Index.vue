
<script>
  // Extensions
  import View from '@/views/View'

  // Mixins
  import LoadSections from '@/mixins/load-sections'

  export default {
    name: 'Home',

    metaInfo: { title: 'Home' },

    extends: View,

    mixins: [
      LoadSections([
        'hero',
        // 'about-our-product',
        // 'features',
        'marketing',
        // 'theme-features',
        'contact-us',
        'recent-works',
        // 'customer-reviews',
        // 'affiliates',
        // 'news',
        'social-media',
        // 'newsletter',
        'info-alt',
      ]),
    ],

    props: {
      id: {
        type: String,
        default: 'home',
      },
    },
  }
</script>
