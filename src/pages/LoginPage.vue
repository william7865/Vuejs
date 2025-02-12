<template>
  <main class="login__main">
    <h1>LoginPage</h1>
    <form @submit.prevent.stop.once="submitHandler">
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
        <button type="reset">Réinitialiser</button>
      </section>
    </form>
  </main>
</template>

<script setup lang="ts">
import { watch, reactive } from "vue";

const data = reactive({
  email: "",
  password: "",
});

const isUserInputValid = (email: string): boolean => {
  const pattern = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
  return pattern.test(email);
};

watch(data, (val) => {
  console.log(val);
});

const submitHandler = () => {
  if (isUserInputValid(data.email)) {
    console.log("Formulaire soumis avec succès");
  } else {
    alert("L'adresse e-mail n'est pas valide");
  }
};

const inputHandler = () => {};
</script>