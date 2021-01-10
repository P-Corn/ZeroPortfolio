<template>
  <div>
    <form 
    name="contact-form" 
    @submit.prevent="sendEmail">
      <base-info-card
      :title="title"
      :subtitle="subtitle"
      space="4"
      color="primary"
      />

      <base-text-field name="name" label="Name" />

      <base-text-field name="company_name" label="Company Name" />

      <base-text-field name="user_email" label="Email" />

      <base-text-field name="subject" label="Subject" />

      <base-textarea
        name="message"
        class="mb-6"
        label="Your Need & Description"
      />

      <base-btn
        type="submit"
        :color="!theme.isDark ? 'accent' : 'white'"
        outlined
      >
      Send message
      </base-btn>
    </form>
  </div>
</template>

<script>

import emailjs from 'emailjs-com';

  export default {
    name: 'BaseContactForm',

    methods: {
      sendEmail: e => {
        emailjs.sendForm('contact_service', 'contact_form', e.target, 'user_WDObBAlbPYJe8ZiZ6VQ9w')
          .then((result) => {
            console.log('SUCCESS!', result.status, result.text);
          }, (error) => {
            console.log('FAILED...', error);
          });
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
