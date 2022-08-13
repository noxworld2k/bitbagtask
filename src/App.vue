<script setup>
import ProductList from "./components/ProductList.vue";
</script>

<template>
  <ProductList/>
</template>

<style lang="scss">
.root {
  font-family: 'Roboto', sans-serif;
  font-size: 16px;
  color: #000;
  margin: 0 auto;
}

.btn {
  background: #0062ff;
  width: 6rem;
  height: 3rem;
  color: #fff;
  border: 0;
  border-radius: 5px;
  margin: 1rem;
  box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);

  &:hover {
    background-color: #0095ff;
  }
}

.btn-green {
  background-color: #79dc63;

  &:hover {
    background-color: #ff0000;
  }
}

.container {
  display: flex;
  flex-wrap: wrap;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  width: 1080px;
  margin: 0 auto;
}


</style>
