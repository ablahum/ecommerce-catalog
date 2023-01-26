<template>
  <div class="wrapper">
    <div class="product__img">
      <!-- <img
        src="../../../product.png"
        alt="product image"
      /> -->
      <img
        :src="product[0].image"
        alt="product image"
      />
    </div>

    <div class="product__content">
      <h1 class="product__title">{{ product[0].title }}</h1>

      <div class="product__spec">
        <p class="product__category">{{ product[0].category }}</p>

        <!-- <ItemRating :rate="product[0].rating.rate" /> -->
        <ItemRating rate="2" />
      </div>

      <hr />

      <p class="product__desc">
        {{ product[0].description }}
      </p>

      <hr />

      <p class="product__price">${{ product[0].price }}</p>

      <div class="buttons">
        <button
          class="btn btn-buy"
          @click="asd"
        >
          Buy now
        </button>

        <button
          class="btn btn-next"
          @click="nextProduct"
        >
          Next product
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import ItemRating from './ItemRating.vue';

export default {
  name: 'ProductItem',

  components: {
    ItemRating,
  },

  props: {
    product: Object,
    asd: Function,
    nextProduct: Function,
  },

  // data() {
  //   return {
  //     product: [],
  //     number: 1,
  //     loading: true,
  //   };
  // },

  // methods: {
  //   getProduct() {
  //     fetch(`https://fakestoreapi.com/products/${this.number}`)
  //       .then((res) => res.json())
  //       .then((data) => {
  //         if (data.category === "men's clothing" || data.category === "women's clothing") {
  //           this.product = data;
  //         } else {
  //           this.product = [];
  //         }
  //         this.loading = false;
  //       })
  //       .catch((err) => console.log(err));
  //   },

  //   nextProduct() {
  //     if (this.number === 20) {
  //       this.number = 1;
  //     } else {
  //       this.number++;
  //     }
  //     this.loading = true;
  //     this.getProduct();
  //   },
  // },

  // mounted() {
  // this.getProduct();
  // },
};
</script>

<style>
.wrapper {
  display: flex;
  padding: 50px;
  max-width: 1000px;
  background-color: var(--white);
  border-radius: 10px;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
}

.product__img {
  margin-right: 50px;
  width: 40%;
}

.product__img img {
  width: 300px;
}

.product__title {
  font-weight: 600;
  color: var(--dark-red);
}

.product__content {
  width: 60%;
}

.product__spec {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 1rem 0 0.5rem;
}

.product__desc {
  margin: 1rem 0 2rem;
  font-size: var(--secondary);
  font-weight: 400;
  color: var(--black);
}

.product__price {
  color: var(--dark-red);
  font-weight: 600;
  margin: 0.5em 0;
}

.buttons {
  display: flex;
  justify-content: space-between;
}

.btn {
  width: 50%;
  padding: 0.5em;
  border: none;
  border-radius: 4px;
  font-weight: 600;
  font-size: var(--secondary);
  cursor: pointer;
}

.btn-buy {
  margin-right: 1em;
  background-color: var(--dark-red);
  color: var(--white);
}

.btn-next {
  background-color: var(--white);
  border: 2px solid var(--dark-red);
  color: var(--dark-red);
}
</style>
