<template>
  <div class="header">
    <div class="header__content">
      <h1 class="header__title">Главнейшая страница</h1>
    </div>
  </div>
</template>

<script>
</script>

<style scoped>
  .header {
    width: 100%;
    height: 100%;
  }
  .header__content {
      width: 100%;
      height: 100%;
      font-size: 14px;
  }
  .header__title {
      width: 100%;
      height: 100%;
      padding: 10px 20px;
      color: #000000;
      font-size: 48px;
  }
  .header__title::after {
    /* content: "|"; */
    /* animation: caret 0.5s infinite alternate; */
    font-weight: 900;
  }
  @keyframes caret {
    0%{opacity: 1;}
    100%{opacity: 0;}
  }
</style>