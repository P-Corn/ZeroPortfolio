<template>
  <div>
    <base-info-card
      :title="title"
      :subtitle="subtitle"
      space="4"
      color="primary"
    />

    <base-text-field label="Name" />

    <base-text-field label="Company Name" />

    <base-text-field label="Email" />

    <base-text-field label="Subject" />

    <base-textarea
      class="mb-6"
      label="Your Need & Description"
    />

    <base-btn
      :color="!theme.isDark ? 'accent' : 'white'"
      href="mailto:shop@vuetifyjs.com?subject=Zero%20Theme%20Question"
      outlined
      target="_blank"
    >
      Send message
    </base-btn>
  </div>
</template>

<script>

import emailjs from 'emailjs-com';

  export default {
    name: 'BaseContactForm',

    methods: {
      sendEmail: (e) => {
        emailjs.sendForm('contact_service', 'contact_form', e.target, 'user_WDObBAlbPYJe8ZiZ6VQ9w')
      }
    },

    // Injected from the Vuetify Themeable mixin
    inject: ['theme'],

    props: {
      subtitle: String,
      title: {
        type: String,
        default: 'MAIL US YOUR MESSAGE',
      },
    },
  }
</script>
