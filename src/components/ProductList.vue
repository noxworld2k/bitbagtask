<template>
  <section class="container">
    <div class="section__product" v-if="productOfTheDay">
      <h1>Produkt dnia</h1>
      <div class="item-list">
        <single-product :product="productOfTheDay"/>
      </div>
    </div>
    <div class="section__product" v-if="bestSales">
      <h1>Wyprzedaż</h1>
      <div class="item-list">
        <single-product v-for="product in bestSales" :product="product"/>
      </div>
    </div>
    <div class="section__product" v-if="recommendedForYou">
      <h1>Wybrane dla Ciebie</h1>
      <div class="item-list">
        <single-product v-for="product in recommendedForYou" :product="product"/>
      </div>
    </div>
  </section>
</template>

<script>
import SingleProduct from "../components/singleProduct.vue";

export default {
  name: "ProductList",
  components: {SingleProduct},
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
          if (data['recommended-for-you']) {
            this.recommendedForYou = data['recommended-for-you'];
          }
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

.section__product {
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin: 20px;
  border-radius: 5px;
  box-shadow: 1px 1px 5px 1px rgba(56, 72, 191, 0.53);

  h1 {
    font-size: 3rem;
  }
}

</style>