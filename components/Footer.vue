<template>
  <footer class="footer">
    <p class="copyright">
      <small>©️{{ new Date().getFullYear() }} k1b3 All Rights Reserved.</small>
    </p>
  </footer>
</template>

<style lang="scss" scoped>
.footer {
  padding: 1em 0;
  background-color: $base-color-secondary;
}

.copyright {
  font-size: fz(14);
  font-family: $font-ubuntu;
  text-align: center;
}
</style>
