<template>
  <form @submit.prevent="submitForm">
    <div class="form-group">
      <label for="name">Product Name</label>
      <input v-model="product.name" type="text" id="name" required />
    </div>
    
    <div class="form-group">
      <label for="price">Price</label>
      <input v-model="product.price" type="number" id="price" required min="0" step="0.01" />
    </div>
    
    <div class="form-group">
      <label for="description">Description</label>
      <textarea v-model="product.description" id="description" required></textarea>
    </div>
    
    <button type="submit">Add Product</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      product: {
        name: '',
        price: null,
        description: ''
      }
    };
  },
  methods: {
    submitForm() {
      this.$emit('add-product', { ...this.product });
      this.product.name = '';
      this.product.price = null;
      this.product.description = '';
    }
  }
};
</script>

<style scoped>
.form-group {
  margin-bottom: 1rem;
}

label {
  display: block;
  margin-bottom: 0.5rem;
}

input, textarea {
  width: 100%;
  padding: 0.5rem;
  margin-bottom: 0.5rem;
}

button {
  padding: 0.5rem 1rem;
  background-color: #007bff;
  color: #fff;
  border: none;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}
</style>
