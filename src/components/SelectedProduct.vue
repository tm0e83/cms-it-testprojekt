<template>
  <div class="product">
    <div class="image">
      <img :src="image" :alt="title">
    </div>
    <div class="details">
      <div class="title">{{title}}</div>
      <div class="price">{{formattedPrice}}</div>
      <button @click="$emit('removeFromBasket', id)" class="alert">Entfernen</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SelectedProduct',
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
    max-width: 60px;

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
</style>
