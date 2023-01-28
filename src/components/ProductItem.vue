<template>
  <div class="wrapper">
    <div class="product__img">
      <img
        :src="product.image"
        alt="product image"
      />
    </div>

    <div>
      <h1
        class="product__title"
        :class="{ men: isMen, women: isWomen }"
      >
        {{ product.title }}
      </h1>

      <div class="product__spec">
        <p class="product__category">{{ product.category }}</p>

        <ItemRating
          :rate="2.5"
          :isMen="isMen"
          :isWomen="isWomen"
        />
      </div>

      <hr />

      <p class="product__desc">
        {{ product.description }}
      </p>

      <hr />

      <p
        class="product__price"
        :class="{ men: isMen, women: isWomen }"
      >
        ${{ product.price }}
      </p>

      <div class="buttons">
        <button
          class="btn btn-buy"
          :class="{ 'btn-men': isMen, 'btn-women': isWomen }"
        >
          Buy now
        </button>

        <button
          class="btn btn-next"
          :class="{ men: isMen, women: isWomen }"
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
    nextProduct: Function,
    isMen: Boolean,
    isWomen: Boolean,
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
  margin-top: -400px;
}

.men {
  color: var(--dark-blue);
}

.women {
  color: var(--dark-red);
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
  color: var(--white);
}

.btn-next {
  background-color: var(--white);
  border: 2px solid;
}

.btn-men {
  background-color: var(--dark-blue);
}

.btn-women {
  background-color: var(--dark-red);
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
