<template>
  <section>
    <h1 class="page_title">Meet the Vendre Team</h1>
    <div class="page_title_animation"></div>
  </section>
</template>

<style scoped>
.page_title {
  font-size: 22pt;
}
.page_title_animation {
  position: relative;
  top: -25px;
  width: 100%;
  height: 3px;
  background-image: linear-gradient(45deg, #5333ed 2%, #ffa2ff 51%, #ff5a20 100%);
  animation: loadTitle 1500ms;
}

@keyframes loadTitle {
  0% {
    width: 0%;
  }
  100% {
    width: 100%;
  }
}
@media (min-width: 1024px) {
  .page_title {
    font-size: 27pt;
  }
  .page_title_animation {
    position: relative;
    top: -30px;
    width: 100%;
    height: 4px;
    background-image: linear-gradient(45deg, #5333ed 2%, #ffa2ff 51%, #ff5a20 100%);
    animation: loadTitle 1500ms;
  }
}
</style>
