<template>
  <div class="home">
    <div class="row">
      <div class="col-12 col-sm-3">
        <sidebar @filter="filterProducts"></sidebar>
      </div>
      <div class="col-12 col-sm-9">
        <cart :products.sync="cartProducts" :total.sync="total"></cart>
        <products :added.sync="addedProduct" @added="addToCart" :filter.sync="filter"></products>
      </div>
    </div>
  </div>
</template>

<script>
import products from '../components/products'
import sidebar from '../components/sidebar'
import cart from '../components/cart'
export default {
  name: 'home',
  components: { products, sidebar, cart },
  data () {
    return {
      cartProducts: [],
      addedProduct: {},
      total: 0,
      filter: ''
    }
  },
  methods: {
    addToCart (item) {
      this.cartProducts.push(item)
      let n = item.price
      n = n.replace('$', '')
      n = n.replace(',', '.')
      this.total = (this.total + parseFloat(n))
      this.loadCart()
    },
    filterProducts (id) {
      this.filter = id
      console.log('filter: ', id)
    },
    loadCart () {
      let cart = this.cartProducts
      if (cart.length > 0) {
        localStorage.setItem('cartProducts', JSON.stringify(cart))
      }
      if (this.total > 0) {
        localStorage.setItem('total', this.total)
      } else {
        this.total = 0
      }
    },
    getCartProducts () {
      let storage = localStorage.getItem('cartProducts')
      if (storage !== '') {
        console.log('Local Storage ', JSON.parse(storage))
        this.cartProducts = JSON.parse(storage)
      } else {
        console.log('vacio')
      }
    }
  },
  created () {
    this.getCartProducts()
  }
}
</script>
