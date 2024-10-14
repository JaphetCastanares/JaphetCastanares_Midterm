<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <div class="home">
      <h1>Welcome to My Vue App</h1>
      <nav>
        <router-link to="/home">Home</router-link>
        <router-link to="/products">Products</router-link>
      </nav>
    </div>
  </template>
  
  <script>
  export default {};
  </script>
  
  <style scoped>
  .home {
    text-align: center;
    padding: 2rem;
    background-image: url('@/assets/background.jpg');
    background-size: cover;
    color: white;
  }
  
  nav {
    margin-top: 20px;
  }
  
  nav a {
    margin-right: 15px;
    color: #000000;
    text-decoration: none;
    font-weight: bold;
  }
  </style>
  