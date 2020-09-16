<template>
  <v-app>
    <nav-bar :cart='cart' @empty-cart="emptyCart"></nav-bar>
    <v-main class="my-10">
      <v-container>
        <p class="text-h5 text-center font-weight-medium mt-3 mb-7">Productos disponibles</p>
        <v-card flat class="my-2" v-for="(product, index) in products" :key="index">
          <v-row no-gutters>
            <v-col cols="10">
              <p class="text-body-1 black--text ma-0">{{product.name}} <span class="mx-3 text-caption">$ {{product.price}}</span></p>
            </v-col>
            <v-col cols="2" class="text-right">
              <v-btn icon color="deep-purple accent-4" @click="addToCart(product)">
                <v-icon small>mdi-plus</v-icon>
              </v-btn>
            </v-col>
          </v-row>
        </v-card>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import NavBar from './components/NavBar'

export default {
  name: 'App',
  components: {
    NavBar
  },
  data: () => ({
    products: [
      { name: 'Caja de frutas', price: 1200 },
      { name: 'Tabla de quesos', price: 10700 },
      { name: 'Pizza congelada', price: 5200 },
      { name: 'Pack bebidas', price: 3900 },
      { name: 'Ensalada surtida', price: 1200 },
      { name: 'Mantel floreado', price: 2300 },
      { name: 'Cuchillos filosos', price: 12500 },
      { name: 'Delantal de cocina', price: 2500 },
      { name: 'Vasos de picnic', price: 2300 },
    ],
    cart: {
      items: [],
      total: null
    }
  }),
  methods: {
    addToCart(item){
      this.cart.items.push(item)
      this.cart.total += item.price
    },
    emptyCart() {
      this.cart.items = []
      this.cart.total = null
    },
  }
};
</script>
