<template>
  <h1 class="heading-1">Inputs</h1>

  <h2 class="heading-2">General info</h2>
  <form @submit.prevent="handleSubmit">
  <UIInput
    v-model:value="vuelidate.nameField.$model"
    label="Your Name"
    name="name"
    placeholder="Enter your name"
    :errors="vuelidate.nameField.$errors"
  />

  <UIInput
    v-model:value="vuelidate.emailField.$model"
    label="Your email"
    name="email"
    placeholder="Enter your email"
    :errors="vuelidate.emailField.$errors"
  />

  <UIInput
    v-model:value="vuelidate.linkField.$model"
    label="Your website"
    name="website"
    placeholder="Enter link to your website"
    :errors="vuelidate.linkField.$errors"
  />

  <h2 class="heading-2">Password confirmation</h2>
  <UIInput
    v-model:value="passwordField"
    label="Your password"
    name="password"
    placeholder="Create your password"
    type="password"
  />
  <UIInput
    v-model:value="vuelidate.confirmedPasswordField.$model"
    label="Your password"
    name="passwordConfirmation"
    placeholder="Confirm your password"
    type="password"
    :errors="vuelidate.confirmedPasswordField.$errors"
  />

    <h2 class="heading-2">Custom rule</h2>
    <UIInput
      v-model:value="vuelidate.frontendField.$model"
      label="Frontend string"
      name="frontend"
      placeholder="Enter string with 'frontend'"
      :errors="vuelidate.frontendField.$errors"
    />

    <UIButton
      :text="formBtnText"
      :color="isFormSubmitted ? 'success' : 'primary'"
    />
  </form>
</template>

<script setup>
import { ref, computed } from 'vue';
import useVuelidate from '@vuelidate/core';
import { helpers, minLength, alpha, email, url, sameAs, required } from '@vuelidate/validators';

import UIInput from '@/components/UIInput.vue';
import UIButton from "@/components/UIButton.vue";

const nameField = ref('');
const emailField = ref('');
const linkField = ref('');
const passwordField = ref('');
const confirmedPasswordField = ref('');
const frontendField = ref('');

const isFormSubmitted = ref(false);
const mustBeFrontend = (value) => value.includes('frontend');

const formBtnText = computed(() => isFormSubmitted.value ? 'Thank you!' : 'Submit')

const rules = computed(() => ({
  // Кастомное сообщение об ошибке с использованием helpers
  nameField: {
    minLength: helpers.withMessage('Минимальная длина: 3 символа', minLength(3)),
    alpha: helpers.withMessage('Ввод цифр запрещён', alpha),
    isRequired: required
  },
  emailField: {
    email: email,
    isRequired: required
  },
  linkField: {
    link: url
  },
  confirmedPasswordField: {
    sameAsPassword: sameAs(passwordField),
    isRequired: required
  },
  frontendField: {
    frontendField: helpers.withMessage('Строка должна содержать слово frontend', mustBeFrontend)
  },
}));

const vuelidate = useVuelidate(rules, { nameField, emailField, linkField, confirmedPasswordField, frontendField });

const handleSubmit = () => {
  vuelidate.value.$touch();

  if (vuelidate.value.$error) return

  alert('Form successfully submitted');
  isFormSubmitted.value = true
};
</script>
