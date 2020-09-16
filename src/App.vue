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
      { name: 'Caja de frutas', price: 1200, qty: 1 },
      { name: 'Tabla de quesos', price: 10700, qty: 1 },
      { name: 'Pizza congelada', price: 5200, qty: 1 },
      { name: 'Pack bebidas', price: 3900, qty: 1 },
      { name: 'Ensalada surtida', price: 1200, qty: 1 },
      { name: 'Mantel floreado', price: 2300, qty: 1 },
      { name: 'Cuchillos filosos', price: 12500, qty: 1 },
      { name: 'Delantal de cocina', price: 2500, qty: 1 },
      { name: 'Vasos de picnic', price: 2300, qty: 1 },
    ],
    cart: {
      items: [],
      total: null
    }
  }),
  methods: {
    addToCart(item){
      let target = this.cart.items.find(p => p.name == item.name)
      if(target){
        target.qty += 1
      } else{
        this.cart.items.push(item)
      }
      this.cart.total += item.price
    },
    emptyCart() {
      this.cart.items = []
      this.cart.total = null
    },
  }
};
</script>
