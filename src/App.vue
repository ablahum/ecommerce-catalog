<template>
  <div class="container">
    <div
      class="bg"
      :class="{ men: isMen, women: isWomen, unavailable: isUnavailable }"
    ></div>
    <SkeletonItem v-if="loading" />

    <ProductItem
      :product="product"
      :loading="loading"
      :nextProduct="nextProduct"
      :isMen="isMen"
      :isWomen="isWomen"
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
      loading: true,
      product: null,
      number: 5,
      isMen: false,
      isWomen: false,
      isUnavailable: true,
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
            switch (data.category) {
              case "men's clothing":
                this.isMen = true;
                this.isWomen = false;
                break;
              case "women's clothing":
                this.isWomen = true;
                this.isMen = false;
                break;
            }

            this.product = data;
          } else {
            // no category
            this.product = null;
            this.isMen = false;
            this.isWomen = false;
          }

          this.loading = false;
        })
        .catch((err) => console.log(err));
    },

    nextProduct() {
      this.loading = true;

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
  flex-direction: column;
  align-items: center;
  height: 100vh;
}

.bg {
  width: 100%;
  height: 60vh;
}

.men {
  background-color: var(--light-blue) !important;
  background-image: url('./assets/pattern.svg');
}

.women {
  background-color: var(--light-red) !important;
  background-image: url('./assets/pattern.svg');
}

.unavailable {
  background-color: var(--light-gray);
}
</style>
