<template>
  <div class="wrapper">
      <h2>Registration</h2>
      <form action="#">
          <div class="input-box">
              <input type="text" v-model="user.firstName" placeholder="Enter your first name" required>
          </div>
          <div class="input-box">
              <input type="text" v-model="user.lastName" placeholder="Enter your last name" required>
          </div>
          <div class="input-box">
              <input type="date" v-model="user.dateOfBirth" placeholder="Enter your date of birth" required>
          </div>
          <div class="input-box">
              <input type="text" v-model="user.country" placeholder="Enter your country" required>
          </div>
          <div class="input-box">
              <input type="text" v-model="user.address" placeholder="Enter your address" required>
          </div>
          <div class="input-box">
              <input type="text" v-model="user.email" placeholder="Enter your email" required>
          </div>
          <div class="input-box">
              <input type="password" v-model="user.password" placeholder="Create password" required>
          </div>
          <div class="input-box button">
              <input type="button" @click="signUp" value="Register Now">
          </div>
          <div class="text">
              <h3>Already have an account? <a href="#">Login now</a></h3>
          </div>
      </form>
  </div>
</template>

<style>
.q-card {
  width: 360px;
}
</style>
<script>
import axios from 'axios'

export default {
    name: "RegisterForm",
    data() {
        return {
            user: {
                firstName: "",
                lastName: "",
                dateOfBirth: "",
                country: "",
                address: "",
                email: "",
                password: ""
            }
        }
    },
    methods: {
        signUp() {
            var url = "https://storedb-api.onrender.com/users"

            axios.post(url, this.user)
                .then(response => {
                    this.$q.notify({
                        message: "Registro satisfactorio",
                        color: "green",
                        position: "top",
                        timeOut: 3000
                    })
                    //Redireccionar al login
                    this.$router.push("/")
                }).catch(error => {

                    this.$q.notify({
                        message: "Ocurrió un error al registrar el usuario",
                        color: "red",
                        position: "top",
                        timeOut: 3000
                    })
                })



        }

    }
}

</script>