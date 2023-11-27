<template>
    <div class="headline-container hidden-sm-and-down">
        <p class="headline-content shipping-content">Free shipping, 30-day return or refund guarentee</p>
    </div>

    <div class="navbar-container d-flex justify-space-between">

        <div>
            <p class="headline-content">advanced development ltd</p>
        </div>

        <div class="navbar-btn-container">

            <v-btn variant="plain" class="btn">
            Home
            </v-btn>
            <v-btn variant="plain" class="btn">
            Sale items
            </v-btn>
            <v-btn variant="plain" class="btn">
            Contact
            </v-btn>
        </div>
        <div class="settings-container">
            <p class="headline-content">Logged in as Joe</p>
        </div>
    </div>
</template>
  
<script>
  export default {
    name: "NavBar",
    data() {
      return {
        
      };
    },
    methods: {
    },
  };
</script>
  
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Abel&family=Fira+Sans:wght@300&display=swap');

    .headline-content {
        color: var(--shades-white, #FFF);
        /* v-text/button */
        font-family: Fira Sans;
        font-size: 14px;
        font-style: normal;
        font-weight: 500;
        line-height: 36px; /* 257.143% */
        letter-spacing: 1.25px;
        text-transform: uppercase;
        text-align: left;
        padding: 0.25%;
        width: 110%;
    }
    .shipping-content {
        padding-left: 10px;
    }

    .headline-container {
        background-color: black;

    }

    .navbar-container {
        background-color: #070707;  
        padding: 10px;
        /*flex-direction: column;*/
    }

    .navbar-btn-container {
        text-align: center;
    }

    .btn {
        color: var(--shades-white, #FFF);
    }

    .settings-container {
        margin-right: 10px;
    }

    @media (max-width: 800px) {

        .navbar-container {
            flex-direction: column;
            text-align: center;
        }

        .headline-content {
            font-size: 12px;
            text-align: center;
            width: 100%;
        }
        

    }

</style>