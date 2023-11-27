<template>
  <div class="website-container">
    <NavBar />
    <v-row md-gutter>
      <v-col cols="3" class="hidden-sm-and-down">
        <BasketCard :basketList="basketList" :key="updateKey"/>
      </v-col>

      <v-col class="shop-container">
        <v-row md-gutter>
          <v-col v-for="(card, index) in paginatedCards" :key="index">
            <div class="shop-widget-container">
              <ShoeCard>
                <template v-slot:image-slot>
                  <v-img
                    height="100%"
                    src="//www.kershkicks.co.uk/cdn/shop/products/Screenshot2023-04-05at15.38.16.png?v=1680705970"
                    cover
                    class="text-white"
                    :key="paginatedCards[index].index"
                  >
                  </v-img>
                </template>
                <template v-slot:price-slot>
                    {{ "£" + paginatedCards[index].price }}
                  </template>
                <template v-slot:brand-slot>
                  {{ paginatedCards[index].brand }}
                </template>
                <template v-slot:model-slot>
                  {{ paginatedCards[index].model }}
                </template>
                <template v-slot:buttons-slot>
                  <v-btn class="more-info-btn" @click="openDialog(paginatedCards[index].index )">More information</v-btn>
                  <v-btn  @click="addToBasket(paginatedCards[index])">Add to basket</v-btn>
                </template>
              </ShoeCard>
            </div>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
    <v-container>
      <v-pagination :length="totalPages" v-model="currentPage"></v-pagination>
    </v-container>

    <v-dialog
      v-model="dialog"
      width="auto"
      class="info-card"
    >
      <v-card>
        <v-card-text>
                <v-img
                    height="100%"
                    width="100%"
                    src="//www.kershkicks.co.uk/cdn/shop/products/Screenshot2023-04-05at15.38.16.png?v=1680705970"
                    cover
                    class="text-white"
                    :key="paginatedCards[this.SelectedIndex].index"
                  >
                  </v-img>
                  <h2 class="fontstyle">
                    {{paginatedCards[this.SelectedIndex].brand}} {{paginatedCards[this.SelectedIndex].model}}
                  </h2>
                  <h3 class="fontstyle">
                    £{{paginatedCards[this.SelectedIndex].price}}
                  </h3>      
                  <br>        
                  <p
                  width="400">Lorem ipsum dolor sit amet consectetur adipisicing elit. Aut, doloribus? Lorem ipsum, dolor sit amet consectetur adipisicing elit. Vel, dolorum.</p>
        </v-card-text>
        <v-card-actions>
          <v-btn class="actions-btn" color="red" @click="dialog = false">Close</v-btn> 
          <v-btn class="actions-btn" color="black" @click="addToBasket(paginatedCards[this.SelectedIndex])">Add to basket</v-btn> 
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
import { defineComponent } from 'vue';

// Components
import NavBar from '../components/NavBar.vue';
import BasketCard from '../components/basketCard.vue';
import ShoeCard from '../components/shoeCard.vue';
import axios from 'axios';

export default defineComponent({
  name: 'HomeView',

  components: {
    NavBar,
    BasketCard,
    ShoeCard,
  },

  data() {
    return {
      currentPage: 1,
      itemsPerPage: 12,
      cards: [],
      dialog: false,
      SelectedIndex: 0,
      basketList: [],
      updateKey: 0,
      isMobileScreen: window.innerWidth >= 768,
    };
  },
  methods: {
    openDialog(indexOfProduct) {
      this.SelectedIndex = indexOfProduct;
      this.dialog = true;
    },
    closeDialog() {
      this.dialog = false;
    },
    addToBasket(item) {
      this.basketList.push(item);
      this.updateKey += 1;
      console.log(this.basketList);
    },
  },
  computed: {
    totalPages() {
      return Math.ceil(this.cards.length / this.itemsPerPage);
    },
    paginatedCards() {
      const start = (this.currentPage - 1) * this.itemsPerPage;
      const end = start + this.itemsPerPage;
      return this.cards.slice(start, end);
    },
  },

  mounted() {

    const apiUrl = 'http://localhost:5054/api/getAllShoesInfo';
    axios.get(apiUrl)
    .then(response => {
      // Handle the successful response here
      console.log('Response data:', response.data);

      //loop through and add to cards list
      response.data.forEach(item => {
        this.cards.push(item);
        //console.log(item.brand);
      });
    })
    .catch(error => {
      // Handle errors here
      console.error('Error:', error);
    });
  
  },
});
</script>

<style scoped>

.website-container {
  background-color: #FFF;
  height:100%;
  overflow-x: hidden;
}

.shop-container {
  margin: 20px;
}

.fontstyle {
    color: var(--black-087, rgba(0, 0, 0, 0.87));
    font-family: Fira Sans;
    font-style: normal;
    font-weight: 500;
    line-height: 36px; /* 257.143% */
    letter-spacing: 1.25px;
    text-transform: uppercase;
  }

  .more-info-btn {
    color: #5b9cce;
  }

  .info-card {
    width: 500px;
  }
  @media (max-width: 768px) {
    .info-card {
      width: 350px;
    }
  }


</style>
