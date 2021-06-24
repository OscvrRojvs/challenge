<template>
  <div class="layout-row wrap justify-content-center">
    <section
      v-for="(product, index) in products"
      :key="index"
      :data-testid="'product-item-' + index"
      class="w-30 product-item"
    >
      <div class="card ma-16">
        <img :src="product.image" class="product-image" :alt="product.name" />
        <div class="card-text pa-4">
          <h5 class="ma-0 text-center">{{ product.name }}</h5>
          <p class="ma-0 mt-8 text-center">${{ product.price }}</p>
        </div>
        <div class="card-actions justify-content-center pa-4">
          <button
            class="x-small outlined"
            data-testid="btn-item-add"
            @click="addProduct(index, product)"
          >
            Add To Cart
          </button>

          <button
            class="x-small danger"
            data-testid="btn-item-remove"
            @click="delProduct(index, product)"
          >
            Remove
          </button>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "ProductList",
  data() {
    return {
      showButton: true,
    };
  },
  props: {
    products: Array,
  },
  methods: {
    addProduct(params, value) {
      let item = value
      this.$emit('add-product', item)
    },
    delProduct(params, value) {
      let item = value
      this.$emit('del-product', item)
    },
  },
};
</script>

<style scoped lang="scss">
.product-image {
  margin: 32px 30%;
  width: 40%;
  min-height: 90px;
}
</style>
