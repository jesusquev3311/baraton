<template>
    <div class="cart">
      <h2 class="cart-title">Shopping Cart</h2>
      <h3 class="cart-subtitle">Your Products</h3>
      <div class="cart-products">
        <div class="row">
          <div v-for="product in products" :key="product.id" class="col-12">
            <div class="product">
              <div class="row">
                <div class="col-sm-4">
                  <div v-if="product.sublevel_id <= 3" class="product-img"><img src="../assets/img/gaseosa.jpg" alt=""></div>
                  <div v-if="product.sublevel_id > 3 && product.sublevel_id <= 7" class="product-img"><img src="../assets/img/desayuno.jpg" alt=""></div>
                  <div v-if="product.sublevel_id > 7 && product.sublevel_id <= 10" class="product-img"><img src="../assets/img/almuerzo.jpg" alt=""></div>
                  <div v-if="product.sublevel_id > 10 && product.sublevel_id <= 13" class="product-img"><img src="../assets/img/vino.jpg" alt=""></div>
                </div>
                <div class="col-sm-8">
                  <h3 class="product-title">{{product.name}}</h3>
                  <div class="product-meta">
                    <span class="product-price">{{product.price}}</span>
                    <span class="product-stock">stock: {{product.quantity}}</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="col-sm-6">
            <div class="total-wrapper">
              <h3 class="total-title">Total:</h3>
              <span>{{total}}</span>
              <span class="cart-btn" @click="checkout" >Checkout</span>
            </div>
          </div>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'cart',
  props: ['products', 'total'],
  data () {
    return {
    }
  },
  methods: {
    checkout () {
      this.$emit('checkout')
    }
  }
}
</script>

<style scoped lang="scss">
  $base-color: #f26d78;
  $title-color: #333;
  $sub-title-color: #8c8c8c;
  .cart{
    text-align: left;
    background-color: #fff;
    border: 1px solid #ededed;
    padding: 20px;
    margin: 30px 0;
    .product{
      padding: 10px;
      border-bottom: 1px solid #ededed;
      margin-bottom: 10px;
      .product-img{
        max-height: 100px;
        img{
          max-height: 100px;
          object-fit: contain;
        }
      }
      .product-meta{
        span{
          display: block;
        }
      }
    }
    .total-wrapper{
      span{
        display: block;
      }
      .cart-btn{
        background-color: $base-color;
        border: 1px solid $base-color;
        color: #fff;
        transition: all .3s;
        cursor: pointer;
        padding: 10px;
        max-width: 150px;
        margin: 20px 0;
        text-align: center;
        font-weight: bold;
        &:hover{
          background-color: #fff;
          color: $base-color;
        }
      }
    }
  }
</style>
