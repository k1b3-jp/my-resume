<template>
  <div class="container">
    <div class="main-visual">
      <div class="main-visual__left">
        <img src="https://placehold.jp/400x400.png" alt="">
      </div>
      <div class="main-visual__right">
        <div class="main-visual__right__name">
          <h2>Kotaro<br>Kibe</h2>
          <h3>Engineer</h3>
        </div>
        <p>自己紹介</p>
      </div>
    </div>

    <section class="experience">
      <h2>Experience</h2>
    </section>

    <section class="sns">
      <h2>SNS</h2>
    </section>

    <section class="activity">
      <h2>Activity</h2>
    </section>
  </div>
</template>

<script>
export default {
  name: 'IndexPage'
}
</script>

<style lang="scss" scoped>
.main-visual {
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start;
  align-items: flex-start;
  &__left {
  }
  &__right {
    &__name {
      display: flex;
      flex-wrap: wrap;
      justify-content: flex-start;
      align-items: center;
    }
  }
}
</style>
