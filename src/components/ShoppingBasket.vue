<template>
  <div class="outer-basket">
    <div class="heading">Warenkorb</div>
    <ul v-if="products.length">
      <li v-for="product in products" :key="product.id">
        <SelectedProduct
          :id="product.id"
          :image="product.thumbnail"
          :title="product.title"
          :price="product.price"
          @removeFromBasket="id => $emit('removeFromBasket', id)"
        />
      </li>
    </ul>
    <p v-else>Keine Produkte ausgewählt</p>
    <div class="sum">Gesamt: {{formattedSum}}</div>
  </div>
</template>

<script>
import SelectedProduct from './SelectedProduct.vue';

export default {
  name: 'ProductList',
  components: {
    SelectedProduct
  },
  props: {
    products: Array
  },
  computed: {
    formattedSum() {
      return new Intl.NumberFormat('de-DE', {
        style: 'currency',
        currency: 'EUR'
      }).format(this.products.reduce((sum, product) => sum += product.price, 0));
    }
  }
}
</script>

<style scoped lang="scss">
  .outer-basket {
    background-color: #f2f2f2;
    padding: 1em;
  }

  .heading {
    font-size: 1.4em;
    margin-bottom: 1em;
    font-weight: bold;
  }

  ul {
    list-style: none;
    margin: 0;
    padding: 0;
  }

  .sum {
    border-top: 1px solid #000;
    padding-top: 0.5em;
    font-size: 1.2em;
    font-weight: bold;
    text-align: right;
  }
</style>