<template>
  <div class="home">
    <h1>Home</h1>
    <form @submit.prevent="logout">
    <button  type="submit">logout</button>
    </form>
  </div>
</template>

<script>
import { logout } from '../components/index'
export default {
  name: 'Home',
  setup() {
    return { logout }
  }
}
</script>
