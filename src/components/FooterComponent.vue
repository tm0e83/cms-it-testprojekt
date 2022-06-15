<template>
  <div class="outer-footer">
    <div class="inner-footer">
      <nav>
        <a href="#">Über uns</a>
        <a href="#">Kontakt</a>
        <a href="#">Impressum</a>
      </nav>
      <span class="copyright">&copy; Timo Ribeiro Szyszka</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'FooterComponent',
}
</script>

<style scoped lang="scss">
  .outer-footer {
    background-color: $primary-color;
    padding: 1rem;
    color: #fff;
    min-height: 225px;
  }

  .inner-footer {
    max-width: $global-width;
    margin: auto;
  }

  nav {
    display: flex;
    flex-direction: column;
    margin-bottom: 1em;
  }

  a {
    color: #fff;
    text-decoration: none;
    margin-bottom: 1.25em;

    &:hover {
      text-decoration: underline;
    }
  }

  .copyright {
    font-size: 0.85em;
  }

  @media (min-width: 40em) {
    .inner-footer {
      display: flex;
      justify-content: space-between;
    }

    nav {
      flex-direction: row;
      margin-bottom: 0;

      a {
        margin-bottom: 0;

        &:not(:first-of-type) {
          margin-left: 2em;
        }
      }
    }
  }
</style>