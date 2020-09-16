<template>
  <v-app>
    <nav-bar></nav-bar>
    <v-main class="my-10">
      <v-container>
        <p class="text-h5 text-center font-weight-medium mt-3">Productos disponibles</p>
        <v-card flat class="my-8" v-for="(product, index) in products" :key="index">
          <v-row>
            <v-col cols="12" md="10">
              <p class="text-h5 black--text">{{product.name}} <span class="mx-3 text-body-1">{{product.price}}</span></p>
            </v-col>
            <v-col cols="12" md="2" class="text-right">
              <v-btn text color="deep-purple accent-4">
                <span class="hidden-md-and-up mr-3">Agregar</span><v-icon>mdi-plus</v-icon>
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
      { name: 'Caja de frutas', price: "$1.200"},
      { name: 'Tabla de quesos', price: "$10.700"},
      { name: 'Pizza congelada', price: "$5.200"},
      { name: 'Pack bebidas', price: "$3.900"},
      { name: 'Ensalada surtida', price: "$1.200"},
    ]
  }),
};
</script>
