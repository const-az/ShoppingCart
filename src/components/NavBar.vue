<template>
  <v-app-bar color="transparent" dense flat absolute class="py-2">
    <v-spacer></v-spacer>
    <v-menu>
        <template v-slot:activator="{ on, attrs }">
          <v-badge :content="cart.items.length" :value="cart.items.length" color="deep-purple accent-4" overlap>
            <v-btn fab depressed small color="transparent" v-bind="attrs" v-on="on">
              <v-icon color="deep-purple accent-4">mdi-cart-outline</v-icon>
            </v-btn>
          </v-badge>
        </template>
        <v-list v-if="cart.items.length!=0">
          <v-list-item v-for="(i, index) in cart.items" :key="index" class="py-0" two-line>
            <v-list-item-content>
              <v-list-item-title class="text-body-2 font-weight-medium">{{i.qty}}x {{i.name}} <span class="text-caption"></span></v-list-item-title>
              <v-list-item-subtitle>${{i.price * i.qty}}</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
          <v-list-item class="text-right">
            <v-list-item-title class="text-body-2 deep-purple--text text--accent-4">Total: <span class="font-weight-bold">${{cart.total}}</span></v-list-item-title>
          </v-list-item>
          <v-list-item>
            <v-btn small outlined rounded color="deep-purple accent-4" @click="emptyCart">Vaciar</v-btn>
            <v-btn small rounded depressed dark class="ml-2" color="deep-purple accent-4">Pagar</v-btn>
          </v-list-item>
        </v-list>
        <v-list v-else>
          <v-list-item>No hay productos</v-list-item>
        </v-list>
      </v-menu>
  </v-app-bar>
</template>

<script>
export default {
  props: {
    cart: {
      type: Object,
      required: true
    }
  },
  methods: {
    emptyCart(){
      this.$emit("empty-cart");
    }
  }
}
</script>