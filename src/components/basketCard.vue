<template>
    <v-card class="basketcard-container"> <!--hidden-sm-and-down-->
    
        <v-card-title>
            Basket
        </v-card-title>
        <v-card-subtitle>
            Sub-total : £{{ this.subtotal }}
        </v-card-subtitle>
            
        <v-card-text>

            <div v-for="(card, index) in this.basketList" :key="index">
              <div class="item-pill">
                {{ this.basketList[index].brand }} {{ this.basketList[index].model }}
                <span class="pill-price">£{{ this.basketList[index].price }}</span>
              </div>

            </div>
        </v-card-text>

        <v-card-actions>
            <v-btn class="checkout-btn">Checkout</v-btn>
        </v-card-actions>
    </v-card>
</template>
  
<script>
  export default {
    name: "BasketCard",
    props: {
          basketList: Array,
          message: String,
        },
    data() {
      
      return {
        subtotal: 0,
      };
    },
    methods: {
      calculateSubtotal() {
        for (let i = 0; i < this.basketList.length; i++) {
          this.subtotal += this.basketList[i].price ; 
        }
      }
    },

    created() {
      console.log(this.basketList)
      console.log(this.message)
      this.calculateSubtotal()
    }
  };
</script>
  
<style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Abel&family=Fira+Sans:wght@500&display=swap');
  .basketcard-container {
    margin: 20px;
    border-radius: 4px;
    background: #e9e9e9;
    color: black/0.87;
    position: fixed;
    width: 23vw;
    height: 80%;
  }

  .item-pill {
    background-color: rgb(199, 197, 197);
    margin: 5px;
    padding: 2%;
    padding-left: 20px;
    padding-right: 20px;
    border-radius: 20px;
    color: var(--black-087, rgba(0, 0, 0, 0.87));
    font-family: Fira Sans;
    font-style: normal;
    font-weight: 500;
    line-height: 36px; /* 257.143% */
    letter-spacing: 1.25px;
    text-transform: uppercase;
    
  }

  .pill-price {
    float: right;
  }

  .checkout-btn {
    margin: auto;
    width: 50%;
    border-radius: 20px;
    color: rgb(64, 104, 64);
    background-color: rgb(184, 218, 184);
  }

</style>