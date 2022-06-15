<template>
  <HeaderComponent/>
  <BodyComponent/>
  <FooterComponent/>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue'
import BodyComponent from './components/BodyComponent.vue'
import FooterComponent from './components/FooterComponent.vue'

export default {
  name: 'App',
  components: {
    HeaderComponent,
    BodyComponent,
    FooterComponent
  }
}
</script>

<style lang="scss">
body {
  padding: 0;
  margin: 0;
  font-size: $global-font-size;
}

#cms-test-projekt {
  font-family: $global-font-family;
  color: $global-font-color;
}

button {
  background-color: $primary-color;
  padding: 0.5rem 1rem;
  border: 0;
  color: #fff;

  &.alert {
    background-color: $alert-color;
  }
}
</style>
