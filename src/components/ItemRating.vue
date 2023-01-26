<template>
  <div class="ratings">
    <p class="rate__number">{{ rate }}</p>

    <div class="rate__graph">
      <div class="rate"></div>

      <div class="rate"></div>

      <div class="rate"></div>

      <div class="rate"></div>

      <div class="rate"></div>
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

<style>
.ratings {
  display: flex;
}

.rate__number {
  margin-right: 5px;
}

/* stars-inner::before {
  content: "\f005 \f005 \f005 \f005 \f005";
  color: #f8ce0b;
}

yg gituan + combine js cocok */

.rate__graph {
  display: flex;
}

.rate {
  width: 18px;
  height: 18px;
  background-color: var(--dark-red);
  border-radius: 100%;
  margin-right: 2px;
}
</style>
