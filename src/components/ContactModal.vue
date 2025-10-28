<template>
  <q-card class="contact-modal" style="min-width: 350px">
    <q-card-section class="row items-center q-pb-none">
      <div class="text-h6">Contact Us</div>
      <q-space />
      <q-btn icon="close" flat round dense v-close-popup />
    </q-card-section>

    <q-card-section>
      <q-form @submit="onSubmit" class="q-gutter-md">
        <q-input
          v-model="form.name"
          label="Name"
          :rules="[val => !!val || 'Name is required']"
        />

        <q-input
          v-model="form.email"
          label="Email"
          type="email"
          :rules="[
            val => !!val || 'Email is required',
            val => /.+@.+\..+/.test(val) || 'Invalid email'
          ]"
        />

        <q-input
          v-model="form.message"
          label="Message"
          type="textarea"
          :rules="[val => !!val || 'Message is required']"
        />

        <div class="row justify-end">
          <q-btn label="Cancel" color="grey" v-close-popup class="q-mr-sm" />
          <q-btn label="Send" type="submit" color="primary" />
        </div>
      </q-form>
    </q-card-section>
  </q-card>
</template>

<script>
import { defineEmits } from 'vue';

const emit = defineEmits(['submit']);

export default {
  name: 'ContactModal',
  data() {
    return {

      form: {
        name: '',
        email: '',
        message: ''
      }
    }
  },
  methods: {
    onSubmit() {
      // Handle form submission here
      console.log('Form submitted:', this.form)
      // Reset form
      this.form = {
        name: '',
        email: '',
        message: ''
      }
      emit('submit');
    }
  }
}
</script>

<style scoped>
.contact-modal {
  padding: 20px;
}
</style>
