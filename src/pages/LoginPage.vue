<template>
  <main class="login__main">
    <h1>LoginPage</h1>
    <form @submit.prevent="submitHandler">
      <section>
        <article>
          <label for="email">Email</label>
          <input
            v-model="data.email"
            type="email"
            id="email"
            placeholder="votre email"
          />
        </article>
        <article>
          <label for="password">Mot de passe</label>
          <input
            v-model="data.password"
            type="password"
            id="password"
            placeholder="votre mot de passe"
          />
        </article>
      </section>
      <section>
        <button type="submit">Se connecter</button>
        <button type="button" @click="resetForm">Réinitialiser</button>
      </section>
    </form>
  </main>
</template>

<script setup lang="ts">
import { reactive } from "vue";

const data = reactive({
  email: "",
  password: "",
});

const isUserInputValid = (email: string): boolean => {
  const pattern = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
  return pattern.test(email);
};

const isPasswordValid = (password: string): boolean => {
  const pattern = /^(?=.*[A-Z])(?=.*\d)[A-Za-z\d]{8,}$/;
  return pattern.test(password);
};

const submitHandler = () => {
  const validEmail = isUserInputValid(data.email);
  const validPassword = isPasswordValid(data.password);

  if (validEmail && validPassword) {
    console.log("Formulaire soumis avec succès");
  } else {
    if (!validEmail) {
      alert("L'adresse e-mail n'est pas valide");
    }
    if (!validPassword) {
      alert("Le mot de passe doit avoir au moins 8 caractères, une lettre majuscule et un chiffre.");
    }
  }
};

const resetForm = () => {
  data.email = "";
  data.password = "";
};
</script>