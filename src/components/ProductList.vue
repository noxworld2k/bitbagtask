<template>
  <section class="container">
    <h1>Produkt dnia</h1>
    <div class="item-list">
      <single-product v-if="productOfTheDay" :product="productOfTheDay"/>
    </div>
    <h1>Wyprzedaż</h1>
    <div class="item-list">
      <single-product v-if="bestSales" v-for="product in bestSales" :product="product"/>
    </div>
    <h1>Wybrane dla Ciebie</h1>
    <div class="item-list">
      <single-product v-if="recommendedForYou" v-for="product in recommendedForYou" :product="product"/>
    </div>
  </section>
</template>

<script>
import Product from "../components/Product.vue";
import SingleProduct from "../components/singleProduct.vue";

export default {
  name: "ProductList",
  components: {SingleProduct, Product},
  data() {
    return {
      bestSales: [],
      productOfTheDay: {},
      recommendedForYou: [],
      productList: {
        'best-sales': [],
        'product-of-a-day': {},
        'recommended-for-you': [],
      }
    }
  },
  mounted() {
    fetch('http://localhost:8082/products')
        .then(response => response.json())
        .then(data => {
          if (data['best-sales']) {
            this.bestSales = data['best-sales'];
          }
          if (data['product-of-a-day']) {
            this.productOfTheDay = data['product-of-a-day'];
          }
          console.log(this.productOfTheDay)
          if (data['recommended-for-you']) {
            this.recommendedForYou = data['recommended-for-you'];
          }
          console.log(data);
        })
  }
}
</script>

<style lang="scss" scoped>
.item-list {
  display: flex;
  flex-wrap: wrap;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  width: 1080px;
  margin: 0 auto;
}

</style>