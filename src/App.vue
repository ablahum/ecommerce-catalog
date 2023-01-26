<template>
  <div class="container">
    <SkeletonItem v-if="loading" />

    <ProductItem
      :product="product"
      :loading="loading"
      :asd="asd"
      :nextProduct="nextProduct"
      v-else-if="product.length > 0"
    />

    <UnavailableProduct v-else />
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
      product: [],
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
      // fetch(`https://fakestoreapi.com/products/${this.number}`)
      // fetch(url(this.number))
      //   .then((res) => res.json())
      //   .then((data) => {
      //     // filter only men's or women's clothing
      //     if (data.category === "men's clothing" || data.category === "women's clothing") {
      //       // get the exact category
      //       if (data.category === "men's clothing") {
      //         this.category === data.category;
      //       } else if (data.category === "women's clothing") {
      //         this.category === data.category;
      //       }

      //       this.product.push(data);
      //     } else {
      //       // no category
      //       this.product = [];
      //     }

      //     this.loading = false;
      //   })
      //   .catch((err) => console.log(err));

      const imgUrl = '../../product.png';

      const data = {
        title: 'ini judul',
        category: "men's clothing",
        image: imgUrl,
        description: 'ini deskripsi fowfowhg owhgow ghowrhgo gohwgohwogwrwo gorwgorwgndog owjgo jfewjf ojwjgp mvrelj waaa!!!!',
        price: 20,
      };

      setTimeout(() => {
        if (data.category === "men's clothing" || data.category === "women's clothing") {
          // get the exact category
          if (data.category === "men's clothing") {
            this.category === data.category;
          } else if (data.category === "women's clothing") {
            this.category === data.category;
          }

          this.product.push(data);
        } else {
          // no category
          this.product = [];
        }

        this.loading = false;
      }, 2000);
    },

    asd() {
      console.log(this.number);
    },

    nextProduct() {
      // product number return to 1
      if (this.number > 20) {
        this.number = 1;
      } else {
        this.number++;
      }

      this.loading = true;
      this.getProduct();
    },
  },

  mounted() {
    this.getProduct();
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
