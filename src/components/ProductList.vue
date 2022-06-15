<template>
  <div class="product-list" v-if="!loading">
    <h1>Unsere Topseller</h1>
    <ul v-if="products.length">
      <li v-for="product in products" :key="product.id">
        <ProductItem
          :id="product.id"
          :image="product.thumbnail"
          :title="product.title"
          :price="product.price"
          @addToBasket="id => $emit('addToBasket', id)"
        />
      </li>
    </ul>
    <p v-else>Sie haben alle Produkte ausgewählt</p>
  </div>
</template>

<script>
import ProductItem from './ProductItem.vue';

export default {
  name: 'ProductList',
  components: {
    ProductItem
  },
  data() {
    return {
      loading: false
    }
  },
  props: {
    products: Array
  },
  created() {
    this.getData();
  },
  methods: {
    getData() {
      this.loading = true;

      fetch("https://dummyjson.com/products?limit=6&skip=3")
        .then(response => response.json())
        .then(json => {
          this.loading = false;
          this.$emit('load', json.products);
        })
        .catch(error => {
          this.loading = false;
          console.log(error);
        });
    }
  }
}
</script>

<style scoped lang="scss">
  .product-list {
    margin: 0 auto;
  }

  h1 {
    margin-top: 0;
  }

  ul {
    list-style: none;
    margin: 0;
    padding: 0;
  }

  @media (min-width: 1000px) {
    ul {
      display: grid;
      grid-template-columns: 1fr 1fr;
    }
  }
</style>
