<template>
  <form @submit.prevent="login">
    <input type="text" placeholder="Email" v-model="email" />
    <input type="password" placeholder="Password" v-model="password" />
    <!-- <a href="#" class="btn" @click="google">
      Login with Google
    </a> -->
    <button type="submit">Submit</button>
    <router-link to="/signup">Need an account?</router-link>

  </form>
</template>

<script>
import { watch, defineComponent } from "vue";
import { user, useLogin } from "./index";
import router from "@/router";
export default defineComponent({
  props: {
    loginReturnUrl: { type: String, default: "/" },
  },
  setup(props) {
    watch(
      () => user.value,
      newUser => {
        if (newUser) {
          router.push(props.loginReturnUrl);
        }
      }
    );
    return {
      ...useLogin()
    };
  },
});
</script>