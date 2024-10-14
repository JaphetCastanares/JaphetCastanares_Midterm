<template>
    <div class="product-form">
      <h2>Add a New Product</h2>
      <form @submit.prevent="submitProduct">
        <div class="form-group">
          <label for="name">Product Name:</label>
          <input v-model="product.name" id="name" type="text" required />
        </div>
        <div class="form-group">
          <label for="price">Price:</label>
          <input v-model="product.price" id="price" type="number" required />
        </div>
        <div class="form-group">
          <label for="description">Description:</label>
          <textarea v-model="product.description" id="description" required></textarea>
        </div>
        <button type="submit">Add Product</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        product: {
          name: '',
          price: 0,
          description: ''
        }
      };
    },
    methods: {
      submitProduct() {
        // Emit the product to the parent component
        this.$emit('add-product', { ...this.product });
        // Clear the form after submitting
        this.product = { name: '', price: 0, description: '' };
      }
    }
  };
  </script>
  
  <style scoped>
  /* Container Styling */
  .product-form {
    max-width: 600px;
    margin: 2rem auto;
    padding: 2rem;
    background-color: #f8f9fa;
    border-radius: 8px;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    font-family: 'Arial', sans-serif;
  }

  /* Form Heading */
  h2 {
    text-align: center;
    font-size: 2rem;
    margin-bottom: 1.5rem;
    color: #343a40;
  }
  
  /* Form Group Styling */
  .form-group {
    margin-bottom: 1.5rem;
  }
  
  label {
    display: block;
    font-size: 1.1rem;
    margin-bottom: 0.5rem;
    color: #495057;
  }
  
  input,
  textarea {
    width: 95%;
    padding: 0.75rem;
    border: 1px solid #ced4da;
    border-radius: 5px;
    font-size: 1rem;
    box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.075);
  }
  
  input:focus,
  textarea:focus {
    outline: none;
    border-color: #80bdff;
    box-shadow: 0 0 5px rgba(0, 123, 255, 0.25);
  }
  
  /* Button Styling */
  button[type="submit"] {
    width: 100%;
    padding: 0.75rem;
    background-color: #28a745;
    border: none;
    color: white;
    font-size: 1.2rem;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  
  button[type="submit"]:hover {
    background-color: #218838;
  }
  </style>
  