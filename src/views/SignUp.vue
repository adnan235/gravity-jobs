<template>
  <div class="sign-up">
    <SignInForm>
      <template #form>
        <div class="form-content">
          <SignUpForm>
            <template #userDetails="userDetails">
              <BaseButton
                @click="signUp(userDetails)"
                title="Sign up"
                variant="flat"
              />
            </template>
          </SignUpForm>
        </div>
      </template>

      <template #optionalNavigation>
        <v-sheet
          class="d-flex flex-wrap align-center justify-center align-self-end"
        >
          <p class="text-center">Don’t have any account?</p>
          <v-btn
            class="text-capitalize"
            variant="text"
            color="primary"
            router
            to="/sign-in"
            >Sign in</v-btn
          >
        </v-sheet>
      </template>
    </SignInForm>
  </div>
</template>

<script setup lang="ts">
import SignUpForm from "@/components/SignUpForm.vue";
import SignInForm from "@/components/SignInForm.vue";
import BaseButton from "@/components/BaseButton.vue";
import type { signUpObject } from "@/types";

import store from "@/store/store";

let signUp = (userDetails: signUpObject) => {
  store.dispatch("signUp", userDetails);
};
</script>

<style scoped lang="scss">
.form-control {
  height: 100%;
  display: grid;
  grid-template-rows: 1fr 40px;
}
</style>
