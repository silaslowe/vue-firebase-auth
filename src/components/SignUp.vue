<template>
  <form @submit.prevent="signup">
    <input type="text" placeholder="Email" v-model="email" />
    <input type="password" placeholder="Password" v-model="password" />
    <!-- <a href="#" class="btn" @click="google">
      Signup with Google
    </a> -->
    <button type="submit">Submit</button>
    <router-link to="/login">Already have an account?</router-link>
  </form>
</template>

<script>
import { watch, defineComponent } from "vue";
import { user, useSignup } from "./index";
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
          console.log(newUser)
          router.push(props.loginReturnUrl);
        }
      }
    );
    return {
      ...useSignup()
    };
  },
});
</script>