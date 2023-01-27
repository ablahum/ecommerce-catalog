<template>
  <div class="wrapper">
    <h1>This product is unavailable to show</h1>

    <button
      class="btn btn-next"
      @click="nextProduct"
    >
      Next product
    </button>
  </div>
</template>

<script>
export default {
  name: 'UnavailableProduct',

  props: {
    nextProduct: Function,
  },
};
</script>

<style scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 50px;
  border-radius: 10px;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
  background-color: var(--white);
  position: absolute;
  top: 25%;
  width: 1000px;
  height: 500px;
  background: #fff url('../assets/sad-face.png') no-repeat center center;
}

h1 {
  font-size: var(--secondary);
  font-weight: 400;
  margin-bottom: 0.6em;
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

.btn-next {
  background-color: var(--white);
  border: 2px solid var(--dark-gray);
  color: var(--dark-gray);
}
</style>
