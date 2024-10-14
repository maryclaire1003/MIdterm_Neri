<template>
  <div>
    <h1>Product Management</h1>
    <ProductList :products="products" @update-product="updateProduct" />
  </div>
</template>

<script>
import ProductList from './ProductList.vue';

export default {
  components: {
    ProductList,
  },
  data() {
    return {
      products: [
        { id: 1, name: 'Product 1', price: 100 },
        { id: 2, name: 'Product 2', price: 200 },
        { id: 3, name: 'Product 3', price: 300 },
      ],
    };
  },
  methods: {
    updateProduct(updatedProduct) {
      const productIndex = this.products.findIndex((product) => product.id === updatedProduct.id);
      if (productIndex !== -1) {
        this.products[productIndex] = updatedProduct;
      }
    },
  },
};
</script>

<style scoped>
h1 {
  color: #333;
}
</style>






