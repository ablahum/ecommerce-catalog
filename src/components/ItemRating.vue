<template>
  <div class="rating">
    <p class="rate__number">{{ rate }}</p>

    <div class="rate__graph">
      <span
        class="rate"
        :class="{ 'rate-unfilled-men': isMen, 'rate-unfilled-women': isWomen }"
        v-for="v in maxValue"
        :key="v"
      >
      </span>

      <div
        class="filled-rates"
        :style="{ width: value + '%' }"
      >
        <div>
          <span
            class="rate"
            :class="{ 'rate-filled-men': isMen, 'rate-unfilled-men': isMen, 'rate-filled-women': isWomen, 'rate-unfilled-women': isWomen }"
            v-for="v in maxValue"
            :key="v"
          >
          </span>
        </div>
      </div>
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
      value: '0',
      maxValue: 5,
    };
  },

  methods: {
    getRatingGraph() {
      this.value = (this.rate / this.maxValue) * 100;
    },
  },

  mounted() {
    this.getRatingGraph();
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
  overflow-x: hidden;
}

.filled-rates div {
  display: flex;
}

.rate {
  width: 18px;
  height: 18px;
  border-radius: 100%;
  margin-left: 0.1rem;
  border: 2px solid;
}

.rate-filled-men {
  background-color: var(--dark-blue);
}

.rate-unfilled-men {
  border-color: var(--dark-blue);
}

.rate-filled-women {
  background-color: var(--dark-red);
}

.rate-unfilled-women {
  border-color: var(--dark-red);
}
</style>
