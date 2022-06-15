<template>
  <div class="outer-body">
    <div>
      <ProductList
        :products="unselectedProducts"
        @load="loadedProducts => setProducts(loadedProducts)"
        @addToBasket="id => addToBasket(id)"
      ></ProductList>
    </div>
    <aside>
      <ShoppingBasket
        :products="selectedProducts"
        @removeFromBasket="id => removeFromBasket(id)"
      ></ShoppingBasket>
    </aside>
  </div>
</template>

<script>
import ProductList from './ProductList.vue';
import ShoppingBasket from './ShoppingBasket.vue';

export default {
  name: 'BodyComponent',
  data() {
    return {
      products: [],
      unselectedProducts: [],
      selectedProducts: []
    }
  },
  components: {
    ProductList,
    ShoppingBasket
  },
  methods: {
    addToBasket(id) {
      this.unselectedProducts = this.unselectedProducts.filter(product => product.id !== id);
      this.selectedProducts = this.selectedProducts.concat(this.products.filter(product => product.id === id));
    },
    removeFromBasket(id) {
      this.selectedProducts = this.selectedProducts.filter(product => product.id !== id);
      this.unselectedProducts = this.unselectedProducts.concat(this.products.filter(product => product.id === id));
    },
    setProducts(loadedProducts) {
      this.products = loadedProducts;
      this.unselectedProducts = loadedProducts;
    }
  }
}
</script>

<style scoped lang="scss">
  .outer-body {
    max-width: $global-width;
    min-height: 600px;
    margin: 25px auto;
    padding: 1rem;
  }

  @media (min-width: 680px) {
    .outer-body {
      display: flex;

      &>div {
        flex: 1;
        margin-right: 1.5em;
      }
    }
  }
</style>
