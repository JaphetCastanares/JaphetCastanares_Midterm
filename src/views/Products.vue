<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <div class="products-page">
      <div class="header">
        <h1>Product Management</h1>
        <nav>
        <router-link to="/home">Home</router-link>
        <router-link to="/products">Products</router-link>
      </nav>
      </div>
      <div class="content">
        <div class="form-section">
          <ProductForm @add-product="addProduct" />
        </div>
        <div class="list-section">
          <ProductList :products="products" @edit-product="editProduct" />
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import ProductForm from '@/components/ProductForm.vue';
  import ProductList from '@/components/ProductList.vue';
  
  export default {
    components: {
      ProductForm,
      ProductList
    },
    data() {
      return {
        products: []
      };
    },
    methods: {
      addProduct(product) {
        this.products.push(product);
      },
      editProduct({ index, product }) {
        this.products.splice(index, 1, product);
      }
    }
  };
  </script>
  
  <style scoped>
  /* Container Styling */
  .products-page {
    font-family: Arial, sans-serif;
    margin: 0 auto;
    margin-top: 10px;
    padding: 20px;
    max-width: 1200px;
    background-color: #f7f9fc;
    border-radius: 10px;
  }
  
  /* Header Section */
  .header {
    text-align: center;
    background-color: #4CAF50;
    color: white;
    padding: 10px;
    border-radius: 8px;
  }
  
  .header h1 {
    margin: 0;
    font-size: 2.5rem;
  }
  
  /* Layout of Form and List */
  .content {
    display: flex;
    justify-content: space-between;
    margin-top: 20px;
  }
  
  /* Form Section */
  .form-section {
    width: 45%;
    background-color: white;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  }
  
  .form-section h2 {
    margin-bottom: 15px;
    font-size: 1.8rem;
  }
  
  .form-section label {
    font-weight: bold;
    display: block;
    margin-bottom: 5px;
  }
  
  .form-section input,
  .form-section textarea {
    width: 100%;
    padding: 10px;
    margin-bottom: 15px;
    border: 1px solid #ddd;
    border-radius: 5px;
    font-size: 1rem;
  }
  
  .form-section button {
    width: 100%;
    padding: 10px;
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 5px;
    font-size: 1.2rem;
    cursor: pointer;
    transition: background-color 0.3s;
  }
  
  .form-section button:hover {
    background-color: #45a049;
  }
  
  /* List Section */
  .list-section {
    width: 50%;
    background-color: white;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  }
  
  .list-section h2 {
    font-size: 1.8rem;
    margin-bottom: 20px;
  }
  
  .list-section ul {
    list-style: none;
    padding: 0;
  }
  
  .list-section li {
    padding: 15px;
    border-bottom: 1px solid #ddd;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .list-section li strong {
    font-size: 1.2rem;
  }
  
  .list-section li p {
    margin: 5px 0;
  }
  
  .list-section li button {
    background-color: #FF5722;
    color: white;
    border: none;
    padding: 10px;
    border-radius: 5px;
    cursor: pointer;
    font-size: 1rem;
    transition: background-color 0.3s;
  }
  
  .list-section li button:hover {
    background-color: #e64a19;
  }
  nav {
    text-align: center;
  }
  
  nav a {
    margin: 0 15px;
    color: #ffffff;
    text-decoration: none;
    font-weight: bold;
  }
  
  nav a:hover {
    text-decoration: underline;
  }
  
  
  /* Responsive Design */
  @media (max-width: 768px) {
    .content {
      flex-direction: column;
    }
  
    .form-section,
    .list-section {
      width: 100%;
      margin-bottom: 20px;
    }
  }
  </style>
  