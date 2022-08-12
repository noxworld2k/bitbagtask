<template>
  <div>
    <div class="product__box">
      <div class="product__box__image">
        <img :src="product.image" alt="{{ product.name }}">
      </div>
      <div v-if="product.badges" class="product__box__title">
        <h1 >{{ product.name }}</h1>
        <span v-if="product.badges['new'] === true" class="badge">Nowość</span>
        <span v-if="product.badges['collection-sale'] === true" class="badge badge-red">Wyprzedaż</span>
          <span v-if="product.badges['last-items'] === true" class="badge badge-blue">Ostatnie sztuki</span>

      </div>
      <div v-if="product.price">
        <p>
          Cena: {{ product.price.current / 100 }} zł
          <s v-if="product.price.current < product.price.regular"
             class="warning-text">{{ product.price.regular / 100 }} zł</s>
        </p>
      </div>
      <div class="product__box__price">
        <p>Stan magazynowy: {{ product.amount }}</p>
      </div>
      <div>
        Ocena: {{ product.rating }}
      </div>
      <div class="product__box__button">
        <button class="btn">Dodaj do koszyka</button>
        <button class="btn">Dodaj do listy życzeń</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "singleProduct",
  props: {
    elementName: String,
    product: Object,
  }
}
</script>

<style lang="scss">

.product__box {
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin: 20px;
  border-radius: 5px;
  box-shadow: 0px 7px 11px -6px rgba(66, 68, 90, 1);

  .product__box__title {
    color: #0062ff;
    display: flex;
    flex-direction: column;
    min-width: 250px;
    h1 {
      text-align: center;
    }
  }

  .product__box__image {
    margin-top: 0.5rem;

    img {
      width: 100%;
      height: 100%;
      border-radius: 5px;
      margin: 0 auto;
    }

  }
}

.warning-text {
  color: red;
}

.badge {
  background-color: #79dc63;
  color: #fff;
  display: inline-block;
  padding-left: 8px;
  padding-right: 8px;
  text-align: center;
  border-radius: 5px;
}

.badge-red {
  background-color: red;
}

.badge-blue {
  background-color: #0062ff;
}

</style>