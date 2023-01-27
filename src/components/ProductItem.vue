<template>
  <div class="wrapper">
    <div class="product__img">
      <img
        :src="product.image"
        alt="product image"
      />
    </div>

    <div>
      <h1 class="product__title men">{{ product.title }}</h1>

      <div class="product__spec">
        <p class="product__category">{{ product.category }}</p>

        <!-- <ItemRating :rate="product.rating.rate" /> -->
        <ItemRating rate="2" />
      </div>

      <hr />

      <p class="product__desc">
        {{ product.description }}
      </p>

      <hr />

      <p class="product__price men">${{ product.price }}</p>

      <div class="buttons">
        <button
          class="btn btn-buy"
          @click="asd"
        >
          Buy now
        </button>

        <button
          class="btn btn-next men"
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
};
</script>

<style scoped>
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
}

.product__img img {
  width: 300px;
}

.product__title {
  font-weight: 600;
}

.product__spec {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 1rem 0 0.5rem;
}

.product__category {
  font-size: 0.7rem;
}

.product__desc {
  margin: 1rem 0 2rem;
  font-size: var(--secondary);
  font-weight: 400;
  color: var(--black);
}

.product__price {
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
  /* background-color: var(--dark-red); */
  /* color: var(--white); */
}

.men {
  color: var(--dark-blue);
  border-color: var(--dark-blue);
}

.women {
  color: var(--dark-red);
  border-color: var(--dark-red);
}

.btn-next {
  background-color: var(--white);
  border: 2px solid;
}

@media screen and (max-width: 576px) {
  .wrapper {
    flex-direction: column;
    align-items: center;
  }

  .product__img {
    margin: 0 0 50px 0;
  }
}
</style>
