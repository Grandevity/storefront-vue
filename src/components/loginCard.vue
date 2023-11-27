<template>
  <div class="page-container">
      <v-card class="card-container d-flex  mb-6 bg-surface-variant"
      tonal
      >
      <div class="form-container">
          <v-form v-model="valid" class="form">
            <h2 class="card-title font">
              Login
            </h2>
            <v-text-field
                    class="input-field-container"
                    v-model="email"
                    label="Email"
                    required
                    hide-details
                  >
            </v-text-field>

            <v-text-field
                    class="input-field-container"
                    v-model="password"
                    label="Password"
                    required
                    hide-details
                  >
            </v-text-field>

            <v-btn type="submit" class="button-container" @click="redirectToHome()">Log in</v-btn>
            <v-btn  class="button-container create-account" @click="redirectToCreateAccount()" >Create Account</v-btn>

          </v-form>

      </div>

      <div class="image-container">
      </div>
    </v-card>
  </div>
</template>
  
<script>
  export default {
    name: "LoginCard",
    data: () => ({
      email: '',
      password: '',
    }),
    methods: {
      redirectToCreateAccount(){
        this.$router.push({ path: '/createaccount'})
        },
        redirectToHome() {
          this.$router.push({ path: '/'})
        }
    },
  };
</script>
  
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Abel&display=swap');


  .page-container {
    background-color: rgb(212, 210, 210);
    width: 100vw;
    height: 100vh;

  }
  .card-container {
    background-color: #e9e6e6;
    width: 80%;
    height: 70%;
    margin: auto;
    top: 50%;
    transform: translate(0, -50%);
    border-radius: 20px;
    filter: drop-shadow(0px 4px 4px rgba(0, 0, 0, 0.25));
  }

  .create-account {
    float: right;
  }

  .input-field-container {
    width: 100%;
    margin: 2%;
    margin-left: 0%;
    background-color: #EEE;
    color: #000;
  }

  .button-container {
    padding-left: 4%;
    padding-right: 4%;
    background-color: #EEE;
    color: #000;

  }

  .card-title {
    color: #000;
    font-size: 48px;
    font-style: normal;
    font-weight: 400;
    line-height: 50px; /* 104.167% */
  }

  .font {
    font-family: 'Abel', sans-serif;
    color: #000;
  }

  .image-container {
    width: 30%;
    height: 100%;
    background-image: url("../assets/images/jordans.png");
    background-size:cover;
    background-position: center;
  }

  .form-container {
    padding: 10%;
    height: 100%;
    width: 70%;
    background-color: white
  }

  .form {
    position: relative;
    top: 50%;
    transform: translate(0, -70%);
  }
</style>