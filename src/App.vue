<template>
  <div class="container type-men">
    <SkeletonItem v-if="loading" />

    <ProductItem
      :product="product"
      :loading="loading"
      :asd="asd"
      :nextProduct="nextProduct"
      v-else-if="product"
    />

    <UnavailableProduct
      v-else
      :nextProduct="nextProduct"
    />
  </div>
</template>

<script>
import { ProductItem, UnavailableProduct, SkeletonItem } from './components';

export default {
  name: 'App',

  components: {
    ProductItem,
    UnavailableProduct,
    SkeletonItem,
  },

  data() {
    return {
      product: null,
      category: null,
      number: 1,
      loading: true,
    };
  },

  methods: {
    url(num) {
      return `https://fakestoreapi.com/products/${num}`;
    },

    getProduct() {
      fetch(this.url(this.number))
        .then((res) => res.json())
        .then((data) => {
          // filter only men's or women's clothing
          if (data.category === "men's clothing" || data.category === "women's clothing") {
            // get the exact category
            if (data.category === "men's clothing") {
              this.category = data.category;
            } else if (data.category === "women's clothing") {
              this.category = data.category;
            }

            this.product = data;
          } else {
            // no category
            this.product = null;
            this.category = null;
          }

          this.loading = false;
        })
        .catch((err) => console.log(err));
    },

    asd() {
      console.log('product =>', this.product);

      console.log('number =>', this.number);
      console.log('category =>', this.category);
    },

    nextProduct() {
      this.loading = true;

      // product number return to 1
      if (this.number >= 20) {
        this.number = 1;
      } else {
        this.number++;
      }

      this.getProduct();
    },
  },

  mounted() {
    this.getProduct();
  },
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.type-default {
  background-color: var(--light-gray);
}

.type-men {
  background-color: var(--light-blue);
  background-image: url('./assets/pattern.svg');
  height: 60vh;
}

.type-women {
  background-color: var(--light-red);
  background-image: url('./assets/pattern.svg');
  height: 60vh;
}
</style>
