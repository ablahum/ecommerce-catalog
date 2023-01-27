<template>
  <div class="ratings">
    <p class="rate__number">{{ rate }}</p>

    <div class="rate__graph">
      <div class="rate men"></div>

      <div class="rate men"></div>

      <div class="rate men"></div>

      <div class="rate men"></div>

      <div class="rate men"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ItemRating',
  props: {
    rate: String,
  },
};
</script>

<style scoped>
.ratings {
  display: flex;
  align-items: center;
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

.rate {
  width: 18px;
  height: 18px;
  border-radius: 100%;
  margin-right: 0.1rem;
}
.men {
  background-color: var(--dark-blue);
}
</style>
