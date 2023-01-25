<template>
  <div class="container">
    <ProductItem />

    <!-- <UnavailableProduct /> -->
  </div>
</template>

<script>
import { ProductItem } from './components';
// import { ProductItem, UnavailableProduct } from './components';

export default {
  name: 'App',
  components: {
    ProductItem,
    // UnavailableProduct,
  },
};
</script>

<style>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: var(--light-red);
}
</style>
