<template>
  <div class="product">
    <div class="image">
      <img :src="image" :alt="title">
    </div>
    <div class="details">
      <div class="title">{{title}}</div>
      <div class="price">{{formattedPrice}}</div>
      <button @click="$emit('addToBasket', id)">Hinzufügen</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductItem',
  props: {
    id: Number,
    image: String,
    title: String,
    price: Number
  },
  computed: {
    formattedPrice() {
      return new Intl.NumberFormat('de-DE', {
        style: 'currency',
        currency: 'EUR'
      }).format(this.price);
    }
  }
}
</script>

<style scoped lang="scss">
  .product {
    display: flex;
    margin-bottom: 1em;
  }

  .image {
    max-width: 90px;

    img {
      max-width: 100%;
    }
  }

  .details {
    margin-left: 1em;
  }

  .price {
    font-weight: 900;
    font-size: 1.3em;
    color: $alert-color;
  }

  @media (min-width: 1000px) {
    .image {
      max-width: 130px;
    }
  }

  @media (min-width: 1300px) {
    .image {
      max-width: 170px;
    }

    .title {
      margin-bottom: 0.25em;
    }

    .price {
      font-size: 1.5em;
      margin-bottom: 0.25em;
    }
  }
</style>
