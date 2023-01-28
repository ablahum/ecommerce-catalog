<template>
  <div class="rating">
    <p class="rate__number">{{ rate }}</p>

    <div
      class="rate__graph"
      @click="getRatingGraph"
    >
      <span
        class="rate"
        :class="{ 'rate-men': isMen, 'rate-women': isWomen }"
        v-for="v in maxValue"
        :key="v"
      >
      </span>

      <div
        class="filled-rates"
        :style="{ width: getRatingGraph + '%' }"
      >
        <!-- <div class="asd"> -->
        <span
          class="rate rate-filled rate-filled-women"
          :class="{ 'rate-men': isMen, 'rate-women': isWomen }"
          v-for="v in maxValue"
          :key="v"
        >
        </span>
      </div>
      <!-- </div> -->
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

  data() {
    return {
      maxValue: 5,
    };
  },

  methods: {
    checkFilledType() {
      // check filled men
      // check filled women
      // if (&& isWomen) {
      //   return true
      // } else if (&& isWomen) {
      //   return false
      // }
    },

    getRatingGraph() {
      return (this.rate / this.maxValue) * 100;
    },
  },
};
</script>

<style scoped>
.rating {
  display: flex;
  align-items: center;
}

.rate__number {
  margin-right: 0.1rem;
  font-size: 0.7rem;
}

.rate__graph {
  display: flex;
  align-items: center;
  position: relative;
}

.filled-rates {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  position: absolute;
  top: 0;

  width: 60%;
}

.rate {
  width: 18px;
  height: 18px;
  border-radius: 100%;
  margin-left: 0.1rem;

  border: 2px solid;
}

.rate-men {
  border-color: var(--dark-blue);
}

.rate-filled-men {
  background-color: var(--dark-blue);
}

.rate-women {
  border-color: var(--dark-red);
}

.rate-filled-women {
  background-color: var(--dark-red);
}
</style>
