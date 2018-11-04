<template>
  <div>
    <h2>Login</h2>
    <form v-on:submit="login">
      <input type="text" name="email" /><br>
      <input type="password" name="password" /><br>
      <input type="submit" value="Login" />
    </form>
  </div>
</template>

<script>
import router from '../router'
import axios from 'axios'
export default {
  name: 'Login',
  data () {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    login: (e) => {
      e.preventDefault()
      const login = () => {
        const data = {
          email: e.target.elements.email.value,
          password: e.target.elements.password.value
        }
        axios.post('/api/login', data)
          .then((response) => {
            console.log('Logged in')
            router.push('/dashboard')
          })
          .catch((errors) => {
            console.log('Cannot log in')
          })
      }
      login()
    }
  }
}
</script>
