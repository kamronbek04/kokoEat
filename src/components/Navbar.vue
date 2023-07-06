<template>
  <nav class="navbar sticky-top">
    <div class="container-fluid wrapper">
      <a href="#asosiy" class="navbar-logo">
        <img :src="logo" alt="koko eat logo" class="logo" />
      </a>
      <div class="d-flex gap-4">
        <a class="auth__sign">
          <i class="bi bi-box-arrow-in-right"></i>
          <span>Sign up</span>
        </a>
        <a class="auth__sign">
          <i class="bi bi-person"></i>
          <span>Log in</span>
        </a>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      logo: 'https://images.squarespace-cdn.com/content/v1/5293a22fe4b0782ba465fe0b/1565372572677-ZWUV5NEKP000OMZTS68B/KOKO+Logo+Lockups+2-02_1200x1200.png?format=1000w',
    };
  },
};
</script>

<style>
.navbar {
  background-color: #fcfcfc;
  padding: 0;
}
.wrapper {
  padding: 0 60px;
  box-shadow: 0 8px 20px rgba(117, 115, 111, 0.2);
}
.logo {
  width: 80px;
  height: 100%;
}
.auth__sign {
  color: #495057;
  display: flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
}
.auth__sign i {
  font-size: 20px;
  color: #212529;
}
.auth__sign span {
  font-size: 20px;
}
</style>
