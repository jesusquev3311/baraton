<template>
  <header>
    <div class="container">
      <div class="row">
        <div class="col-12 col-sm-4">
          <div class="logo">{{ logoText }}</div>
        </div>
        <div class="col-12 col-sm-8">
          <div class="cart-wrapper">
            <img src="../assets/img/cart.png" alt="carrito">
          </div>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'header',
  data () {
    return {
      logoText: 'EL BARATON'
    }
  }
}
</script>

<style scoped lang="scss">
  $base-color: #f26d78;
  header{
    background-color: $base-color;
    padding: 20px 0;
    text-align: left;
    .logo{
      color:#fff;
      font-weight: bold;
      font-size: 32px;
    }
    .cart-wrapper{
      text-align: right;
      img{
        max-height: 50px;
        cursor: pointer;
      }
    }
  }
</style>
