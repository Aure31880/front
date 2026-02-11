<template>
  <form @submit.prevent="login">
    <input v-model="username" placeholder="Username" />
    <input v-model="password" type="password" placeholder="Password" />
    <button type="submit">Login</button>
  </form>
</template>

<script>
import { ref } from 'vue'
import axios from "axios"
import { useRouter } from "vue-router"

export default {
  setup() {
    const router = useRouter()
    const username = ref("")
    const password = ref("")

    const login = async () => {
      try {
        const res = await axios.post("http://127.0.0.1:8000/login", {
          username: username.value,
          password: password.value
        })
        localStorage.setItem("access_token", res.data.access_token)
        router.push("/dashboard") // redirige vers la page admin
      } catch (err) {
        alert("Login failed")
      }
    }

    return { username, password, login }
  }
}
</script>
