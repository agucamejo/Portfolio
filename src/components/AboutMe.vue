<template>
    <div class="about-me-container ">
      <img src="../assets/images/Foto CV.jpeg" alt="Mi Foto" class="about-me-image">
      <div class="about-me-details">
        <h1 class="text-5xl text-red-400 font-bold mt-2 mb-2">AGUSTIN CAMEJO</h1>
        <h3 class="text-2xl font-semibold">FRONT-END DEVELOPER</h3>
        <p class="text-lg mt-2">Programador enfocado en la creación de experiencias de usuario atractivas y optimizadas. Comprometido con el aprendizaje constante para contribuir al mundo digital y aportar soluciones a clientes reales.</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'AboutMe',
  };
  </script>
  
  <style scoped>

  .about-me-container {
    max-width: 70%;
    margin: 3rem auto; 
    display: grid;
    grid-template-columns: auto 1fr;
    gap: 40px;
    align-items: center;
  }
  
  .about-me-image {
    width: 200px;
    height: 200px;
    object-fit: cover;
    border-radius: 80%;
  }

  @media (max-width: 768px) {
    .about-me-image {
      float: none;
      display: block;
      margin: 0 auto;
      width: 200px;
      height: 200px;
      object-fit: cover;
      border-radius: 80%;
    }

    .about-me-container {
      display: grid;
      grid-template-columns: auto ;
      justify-content: center;
      align-content: center;
      text-align: center;
    }
  }
  </style>
  