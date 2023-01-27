<template>
  <div class="rating">
    <p class="rate__number">{{ rate }}</p>

    <div class="rate__graph">
      <div
        class="rate-fill"
        :class="{ men: isMen, women: isWomen }"
      ></div>

      <div
        class="rate-fill"
        :class="{ men: isMen, women: isWomen }"
      ></div>

      <div
        class="rate-fill"
        :class="{ men: isMen, women: isWomen }"
      ></div>

      <div
        class="rate-fill"
        :class="{ men: isMen, women: isWomen }"
      ></div>

      <div
        class="rate-fill"
        :class="{ men: isMen, women: isWomen }"
      ></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ItemRating',

  props: {
    rate: Number,
    isMen: Boolean,
    isWomen: Boolean,
  },
};
</script>

<style scoped>
.rating {
  display: flex;
  align-items: center;
}

.men {
  background-color: var(--dark-blue);
}

.women {
  background-color: var(--dark-red);
}

/* stars-inner::before {
  content: "\f005 \f005 \f005 \f005 \f005";
  color: #f8ce0b;
}

yg gituan + combine js cocok */

.rate__number {
  margin-right: 0.2rem;
  font-size: 0.7rem;
}

.rate__graph {
  display: flex;
}

.rate-fill {
  width: 18px;
  height: 18px;
  border-radius: 100%;
  margin-right: 0.1rem;
}
</style>
