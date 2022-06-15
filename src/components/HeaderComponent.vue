<template>
  <div class="outer-header">
    <div class="inner-header">
      <span>CMS-IT</span> Testprojekt
    </div>
  </div>
</template>

<script>
export default {
  name: 'HeaderComponent',
  props: {}
}
</script>

<style scoped lang="scss">
  .outer-header {
    box-shadow: 0 0 5px 0 rgba(180, 180, 180, 0.5);
    padding: 1.5em 1rem;
    color: #8b8b8b;
  }

  .inner-header {
    max-width: $global-width;
    margin: auto;
  }

  span {
    font-size: 1.25em;
    font-weight: 900;
    color: $primary-color;
  }
</style>
