<template>
  <div
    id="aksiyalar"
    class="carousel slide discount-wrapper"
    data-bs-ride="true"
  >
    <div class="carousel-inner">
      <div class="carousel-item active">
        <img
          src="https://logojinni.com/image/logos/koko.svg"
          class="d-block w-75"
          alt="..."
        />
      </div>
      <div class="carousel-item">
        <img
          src="https://www.logotypes101.com/logos/967/C50D81DC807DA4E46C2DB64AF0DE93B6/Goya.png"
          class="d-block w-75"
          alt="..."
        />
      </div>
      <div class="carousel-item">
        <img
          src="https://www.logotypes101.com/logos/967/C50D81DC807DA4E46C2DB64AF0DE93B6/Goya.png"
          class="d-block w-75"
          alt="..."
        />
      </div>
    </div>
    <button
      class="carousel-control-prev"
      type="button"
      data-bs-target="#carouselExampleRide"
      data-bs-slide="prev"
    >
      <span class="carousel-control-prev-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Previous</span>
    </button>
    <button
      class="carousel-control-next"
      type="button"
      data-bs-target="#carouselExampleRide"
      data-bs-slide="next"
    >
      <span class="carousel-control-next-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Next</span>
    </button>
  </div>
</template>
<style scoped>
.discount-wrapper {
  width: 850px;
  height: 85vh;
  margin: 18px;
}
.carousel-item img {
  width: 100% !important;
  height: 100vh;
}
</style>
