<template>
  <div class="container">
    <div class="mb-10 text-center">
      <h1 class="mb-2 text-xl font-bold">Bolão do Oscar {{ currentYear }}</h1>
      <p>Faça o login para começar a votar</p>
    </div>

    <FormKit
      type="form"
      class-name="w-full"
      submit-label="Entrar"
      :actions="false"
      :config="{
        validationVisibility: 'submit',
        incompleteMessage: false,
      }"
      :classes="{
        submit: {
          'bg-blue-500': true,
        },
      }"
      @submit="userStore.logIn"
    >
      <FormKit
        type="email"
        name="username"
        placeholder="Username"
        validation="required|email"
        :outer-class="{
          'max-w-[20em]': false,
        }"
        :validation-messages="{
          required: 'Username é obrigatório',
          email: 'Username precisa ser um e-mail',
        }"
      />

      <FormKit
        type="password"
        name="password"
        placeholder="Senha"
        validation="required"
        :outer-class="{
          'max-w-[20em]': false,
        }"
        :validation-messages="{
          required: 'Senha é obrigatória',
        }"
      />

      <FormKit
        type="submit"
        label="Entrar"
        :classes="{
          outer: {
            'max-w-\[20em\]': false,
          },
          input: {
            'w-full': true,
            'justify-center': true,
          },
        }"
      />
    </FormKit>

    <hr class="mx-auto my-8 max-w-[50%]" />

    <div class="mb-4 text-center">
      <p class="text-sm">
        Não tem uma conta?
        <router-link to="/cadastro" class="underline">Cadastre-se</router-link>
        | Esqueceu a senha?
        <router-link to="/esqueci-minha-senha" class="underline"
          >Clique aqui para recuperar</router-link
        >
      </p>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { useUserStore } from '@/stores';

const userStore = useUserStore();

const currentYear = new Date().getFullYear();
</script>
