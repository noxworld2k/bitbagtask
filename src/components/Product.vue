<template>
<div class="product__box"  v-if="productList" v-for="product in productList">
      <div class="product__box__image">
        <img :src="product.image" alt="">
      </div>
      <div class="product__box__title">
        <h1>{{ product.name }}</h1>
      </div>
      <div class="product__box__price" v-if="product.price">
        <p>
          Cena: {{ product.price.current / 100 }} zł
          <s v-if="product.price.current < product.price.regular"
             class="warning-text">{{ product.price.regular / 100 }} zł</s>
        </p>
      </div>
      <div>
        <p>Stan magazynowy: {{ product.amount }}</p>
      </div>
      <div>
        Ocena: {{ product.rating }}
      </div>
      <div class="product__box__button">
        <button class="btn" >Dodaj do koszyka</button>
        <button v-if='product.added-to-wishlist' disabled>Na liście życzeń</button>
        <button v-else class="btn" >Dodaj do listy życzeń</button>
    </div>
  </div>
</template>

<script>

export default {
  name: "product",
  props: {
    productList: Array
  },
}
</script>

<style lang="scss" scoped>

</style>
