<template>
  <div class="wrapper">
    <div class="product__img">
      <img
        :src="product.image"
        alt="product image"
      />
    </div>

    <div class="product__content">
      <h1 class="product__title">{{ product.title }}</h1>

      <div class="product__spec">
        <p class="product__category">{{ product.category }}</p>

        <ItemRating :rate="product.rating.rate" />
      </div>

      <hr />

      <p class="product__desc">
        {{ product.description }}
      </p>

      <hr />

      <p class="product__price">${{ product.price }}</p>

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
    type: String,
  },

  methods: {
    asd() {
      console.log(this.product.category);
    },
    getProduct() {
      fetch(`https://fakestoreapi.com/products/${this.number}`)
        .then((res) => res.json())
        .then((data) => {
          this.product = data;
        })
        .catch((err) => console.log(err));
    },
    nextProduct() {
      this.number++;
      this.getProduct();
    },
  },

  data() {
    return {
      product: [],
      number: 1,
    };
  },

  mounted() {
    this.getProduct();
  },
};
</script>

<style>
.wrapper {
  display: flex;
  padding: 50px;
  max-width: 1034px;
  background-color: var(--white);
  border-radius: 10px;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
}

.product__img {
  margin-right: 67.68px;
}

.product__img img {
  width: 300px;
}

.product__title {
  margin-bottom: 25px;
  font-weight: 600;
  color: var(--dark-red);
  font-size: 28px;
}

.product__title-men {
  color: var(--dark-blue);
  margin-bottom: 25px;
  font-weight: 600;
  font-size: 28px;
}

.product__spec {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 11px;
}

.product__desc {
  margin: 26px 0 62.5px;
  font-size: 20px;
  font-weight: 400;
  color: var(--black);
}

.product__price {
  color: var(--dark-red);
  font-size: 28px;
  font-weight: 600;
  margin: 15px 0;
}

.buttons {
  display: flex;
  justify-content: space-between;
}

.btn {
  width: 50%;
  padding: 9px;
  border: none;
  border-radius: 4px;
  font-weight: 600;
  font-size: 20px;
  cursor: pointer;
}

.btn-buy {
  margin-right: 19px;
  background-color: var(--dark-red);
  color: var(--white);
}

.btn-next {
  background-color: var(--white);
  border: 2px solid var(--dark-red);
  color: var(--dark-red);
}
</style>
