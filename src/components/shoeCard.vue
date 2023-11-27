<template>
    <v-card class="shoecard-container">
        <div class="image-container">
          <slot name="image-slot"></slot>
        </div>
        <v-card-title class="shoe-brand fontstyle">
          <slot name="model-slot">Brand</slot> <br>
          <v-card-subtitle class="shoe-sub fontstyle">
            <slot name="brand-slot">Model</slot>
          </v-card-subtitle>
        </v-card-title>
        <div class="price fontstyle">
          <slot name="price-slot"></slot>
        </div>
          

        <v-card-actions class="d-flex justify-space-evenly">
          <slot name="buttons-slot">
            </slot>
        </v-card-actions>
    </v-card>
</template>
  
<script>
  export default {
    name: "ShoeCard",
    data() {
      return {
      };
    },
    methods: {
    },
  };
</script>
  
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Abel&family=Fira+Sans:wght@500&display=swap');

  .fontstyle {
    color: var(--black-087, rgba(0, 0, 0, 0.87));
    font-family: Fira Sans;
    font-style: normal;
    font-weight: 500;
    line-height: 36px; /* 257.143% */
    letter-spacing: 1.25px;
    text-transform: uppercase;
  }
  .shoecard-container {
    color: black/0.87;
    border-radius: 20px;
    background: #F5F5F5;
    box-shadow: 0px 4px 4px 0px rgba(0, 0, 0, 0.25);
  }
  .shoe-sub {
    margin-top: -10px;
    text-align: center;
    font-size: 14px;

  }
  .price {
    margin-top: -10px;
    text-align: center;
    font-size: 14px;
  }

  .shoe-brand {
    text-align: center;
    font-size: 19px;
  }

</style>