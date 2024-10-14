<script setup>
import { ref } from 'vue';
import { defineEmits } from 'vue';
const emit = defineEmits(['add-product']);
const productName = ref('');
const productPrice = ref('');
const productDescription = ref('');
const handleSubmit = () => {
  emit('add-product', {
    name: productName.value,
    price: productPrice.value,
    description: productDescription.value,
  });
  productName.value = '';
  productPrice.value = '';
  productDescription.value = '';
};
</script>

<template>
  <form @submit.prevent="handleSubmit" class="product-form">
    <div class="form-group">
      <label for="name">Product Name:</label>
      <input v-model="productName" type="text" id="name" placeholder="Enter product name" required />
    </div>

    <div class="form-group">
      <label for="price">Price:</label>
      <input v-model="productPrice" type="number" id="price" placeholder="Enter product price" required />
    </div>

    <div class="form-group">
      <label for="description">Description:</label>
      <textarea v-model="productDescription" id="description" placeholder="Enter product description" required></textarea>
    </div>

    <button type="submit">Add Product</button>
  </form>
</template>

<style scoped>
.product-form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  background-color: white;
  padding: 1.5rem;
  border-radius: 8px;
  box-shadow: 0px 2px 8px rgba(0, 0, 0, 0.1);
}

.form-group {
  display: flex;
  flex-direction: column;
}

label {
  font-weight: bold;
  margin-bottom: 0.5rem;
}

input,
textarea {
  padding: 0.75rem;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 1rem;
}

button {
  padding: 0.75rem;
  background-color: var(--primary-color);
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: darken(var(--primary-color), 10%);
}
</style>
