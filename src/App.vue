<template>
  <div>
    <ProductItem />

    <UnavailableProduct />
  </div>
</template>

<script>
import { ProductItem, UnavailableProduct } from './components';

export default {
  name: 'App',
  components: {
    ProductItem,
    UnavailableProduct,
  },
};
</script>
