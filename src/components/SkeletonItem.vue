<template>
  <div class="skeleton">
    <div class="skeleton__img"></div>

    <div class="skeleton__content">
      <h1 class="skeleton__title"></h1>

      <p class="skeleton__spec">
        <span></span>

        <span></span>
      </p>

      <p class="skeleton__desc">
        <span></span>

        <span></span>

        <span></span>
      </p>

      <div class="skeleton__buttons">
        <a
          href="#"
          class="skeleton__btn"
        ></a>

        <a
          href="#"
          class="skeleton__btn"
        ></a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SkeletonItem',
};
</script>

<style>
.skeleton {
  display: flex;
  padding: 50px;
  max-width: 1000px;
  background-color: var(--white);
  border-radius: 10px;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
}

.skeleton__img {
  width: 300px;
  height: 300px;
  border-radius: 50%;
  margin-right: 50px;
  animation: pulse 2s infinite ease-in-out;
}

.skeleton__content {
  display: flex;
  flex-direction: column;
  width: 300px;
  height: 300px;
}

.skeleton__title {
  width: 300px;
  height: 24px;
  margin-bottom: 25px;
  animation: pulse 2s infinite ease-in-out;
}

.skeleton__spec {
  display: flex;
  justify-content: space-between;
  margin-bottom: 11px;
}

.skeleton__spec span {
  width: 90px;
  height: 18px;
  animation: pulse 2s infinite ease-in-out;
}

.skeleton__desc {
  margin: 26px 0 62.5px;
}

.skeleton__desc span:nth-child(odd) {
  display: block;
  width: 250px;
  height: 20px;
  animation: pulse 2s infinite ease-in-out;
}

.skeleton__desc span:nth-child(2) {
  display: block;
  width: 150px;
  height: 20px;
  animation: pulse 2s infinite ease-in-out;
  margin: 5px 0;
}

.skeleton__buttons {
  display: flex;
  justify-content: space-between;
  margin-top: 15px;
}

.skeleton__btn {
  width: 50%;
  height: 24px;
  animation: pulse 2s infinite ease-in-out;
}

.skeleton__btn:nth-child(1) {
  margin-right: 19px;
}

@keyframes pulse {
  0% {
    background-color: #94a3b8;
  }

  50% {
    background-color: #cbd5e1;
  }

  100% {
    background-color: #94a3b8;
  }
}
</style>
