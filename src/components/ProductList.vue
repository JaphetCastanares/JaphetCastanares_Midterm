<template>
    <div class="product-list">
      <h2>Product List</h2>
      <ul v-if="products.length">
        <li v-for="(product, index) in products" :key="index" class="product-item">
          <div v-if="editingIndex === index" class="edit-mode">
            <input v-model="editingProduct.name" type="text" placeholder="Product Name" />
            <input v-model="editingProduct.price" type="number" placeholder="Price" />
            <textarea v-model="editingProduct.description" placeholder="Description"></textarea>
            <button @click="saveProduct(index)">Save</button>
          </div>
          <div v-else>
            <strong>{{ product.name }}</strong> - ₱{{ product.price }}
            <p>{{ product.description }}</p>
            <button @click="editProduct(index)">Edit</button>
          </div>
        </li>
      </ul>
      <p v-else>No products available.</p>
    </div>
  </template>
  
  <script>
  export default {
    props: ['products'],
    data() {
      return {
        editingIndex: null,
        editingProduct: null,
      };
    },
    methods: {
      editProduct(index) {
        this.editingIndex = index;
        this.editingProduct = { ...this.products[index] };
      },
      saveProduct(index) {
        this.$emit('edit-product', { index, product: this.editingProduct });
        this.editingIndex = null;
      }
    }
  };
  </script>
  
  <style scoped>
  /* Container Styling */
  .product-list {
    padding: 2rem;
    max-width: 700px;
    margin: 2rem auto;
    background-color: #f7f7f7;
    border-radius: 10px;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    font-family: 'Arial', sans-serif;
  }
  
  h2 {
    text-align: center;
    font-size: 2rem;
    margin-bottom: 1.5rem;
    color: #343a40;
  }
  
  /* Product List Styling */
  ul {
    list-style: none;
    padding: 0;
  }
  
  li {
    margin-bottom: 1.5rem;
    padding: 1rem;
    background-color: #ffffff;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
    transition: box-shadow 0.2s ease;
  }
  
  li:hover {
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
  }
  
  /* Product Info Styling */
  strong {
    font-size: 1.3rem;
    color: #343a40;
  }
  
  p {
    color: #555;
    margin: 0.5rem 0;
  }
  
  /* Edit Button Styling */
  button {
    background-color: #007bff;
    color: white;
    border: none;
    padding: 0.5rem 1rem;
    font-size: 1rem;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  
  button:hover {
    background-color: #0056b3;
  }
  
  /* Edit Mode Styling */
  .edit-mode input,
  .edit-mode textarea {
    width: 100%;
    padding: 0.5rem;
    margin-bottom: 0.5rem;
    border: 1px solid #ced4da;
    border-radius: 5px;
  }
  
  .edit-mode button {
    width: 100%;
    background-color: #28a745;
  }
  
  .edit-mode button:hover {
    background-color: #218838;
  }
  </style>
  