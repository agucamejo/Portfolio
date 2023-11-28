<template>
    <div class="project-gallery-container">
      <div v-for="(project, index) in projects" :key="index" class="project-card">
        <img :src="project.image" :alt="project.name" class="project-image">
        <div class="project-details">
          <h2 class="text-lg font-bold">{{ project.name }}</h2>
          <p class="mt-2">{{ project.description }}</p>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import project1Image from '../assets/images/Foto CV.jpeg';
  import CryptoSafe from '../assets/images/cryptosafe.jpeg';
  import Streetwear from '../assets/images/streetwear.jpeg';
  import Globo from '../assets/images/globo.jpeg';

  export default {
    name: 'ProjectGallery',
    data() {
      return {
        projects: [
          {
            name: 'Resto BRK',
            image: project1Image,
            description: 'Administrador de restaurante.',
          },
          {
            name: 'CryptoSafe',
            image: CryptoSafe,
            description: 'E-wallet de criptomonedas.',
          },
          {
            name: 'Globo',
            image: Globo,
            description: 'Perfil de red social.',
          },
          {
            name: '1998-Streetwear',
            image: Streetwear,
            description: 'E-commerce de ropa urbana.',
          },
          {
            name: 'Cine UTN',
            image: project1Image,
            description: 'Administrador de cine.',
          }
        ],
      };
    },
  };
  </script>
  
  <style scoped>
  .project-gallery-container {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: 50px;
  }
  
  .project-card {
    position: relative;
    overflow: hidden;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(255, 255, 255, 0.1);
    transition: box-shadow 0.3s ease;
  
    &:hover {
      box-shadow: 0 8px 12px rgba(255, 255, 255, 0.2);
    }
  }
  
  .project-image {
    width: 100%;
    height: 180px; 
    object-fit: cover;
  }
  
  .project-details {
    padding: 16px;
  }
  </style>
  