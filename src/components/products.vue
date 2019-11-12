<template>
    <div class="products-wrapper">
      <div class="row">
        <div v-for="product in products" :key="product.id" class="col-12 col-sm-3">
            <div class="product">
              <div v-if="product.sublevel_id <= 3" class="product-img"><img src="../assets/img/gaseosa.jpg" alt=""></div>
              <div v-if="product.sublevel_id > 3 && product.sublevel_id <= 7" class="product-img"><img src="../assets/img/desayuno.jpg" alt=""></div>
              <div v-if="product.sublevel_id > 7 && product.sublevel_id <= 10" class="product-img"><img src="../assets/img/almuerzo.jpg" alt=""></div>
              <div v-if="product.sublevel_id > 10 && product.sublevel_id <= 13" class="product-img"><img src="../assets/img/vino.jpg" alt=""></div>
              <h3 class="product-title">{{product.name}}</h3>
              <div class="product-meta">
                <span class="product-price">{{product.price}}</span>
                <span class="product-stock">stock: {{product.quantity}}</span>
                <span v-if="product.available" class="product-stock">available: {{available}}</span>
                <span v-else class="product-status">{{notAvailable}}</span>
              </div>
              <div class="product-btn-wrapper">
                <span class="product-btn" @click="addToCart(product)">Add</span>
              </div>
            </div>
        </div>
      </div>
    </div>
</template>

<script>
import products from '../data/products'
export default {
  name: 'products',
  props: ['added'],
  data () {
    return {
      products: products.products,
      available: 'available',
      notAvailable: 'not available'
    }
  },
  methods: {
    addToCart (product) {
      this.$emit('added', product)
    }
  }
}
</script>

<style scoped lang="scss">
  $base-color: #f26d78;
  $title-color: #333;
  $sub-title-color: #8c8c8c;
  .products-wrapper{
    padding: 40px 0;
    .product{
      margin-bottom: 50px;
      .product-img{
        height: 185px;
        overflow: hidden;
        max-height: 185px;
        img{
          width: 100%;
          object-fit: contain;
          height: 185px;
          background-color: white;
        }
      }
      .product-meta{
        span{
          display: block;
        }
      }
      .product-btn-wrapper{
        .product-btn{
          background-color: $base-color;
          color: #fff;
          display: block;
          border-radius: 30px;
          padding: 5px 0;
          margin: 20px 0;
          cursor:pointer;
          border:1px solid $base-color;
          transition: all .3s;
          &:hover{
            color: $base-color;
            background-color: #fff;
            border: 1px solid $base-color;
          }
        }
      }
    }
  }
</style>
