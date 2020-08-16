<template functional>
  <div class="card">
    <slot></slot>
  </div>
</template>

<style scoped lang="stylus">
.card
  background #fff
  box-shadow 0 0 20px rgba(0, 0, 0, 0.5)
  border-radius 5px
  padding 40px 15%

  @media screen and (max-width: 480px)
    padding 20px 10%
</style>
