<template>
  <div class="project-container">
    <h2 class="text-4xl font-semibold mb-6 color">PROYECTOS</h2>
    <div class="project-gallery-container"> 
      <div v-for="(project, index) in projects" :key="index" class="project-card">
        <img :src="project.image" :alt="project.name" class="project-image">
        <div class="project-details">
          <h2 class="text-lg font-bold">{{ project.name }}</h2>
          <p class="mt-1">{{ project.description }}</p>
          <small class="text-xs text-gray-600">
            <span v-for="(tech, index) in project.technologies" :key="index">
              {{ tech }}
              <template v-if="index !== project.technologies.length - 1">&#183; </template>
            </span>
          </small>
          <div class="flex items-center">
            <a v-if="project.repo" :href="project.repo" target="_blank" rel="noopener noreferrer">
              <svg class="mt-3 mr-2" width="24" height="24" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path fill="#000000" d="M12 1A10.89 10.89 0 0 0 1 11.77A10.79 10.79 0 0 0 8.52 22c.55.1.75-.23.75-.52v-1.83c-3.06.65-3.71-1.44-3.71-1.44a2.86 2.86 0 0 0-1.22-1.58c-1-.66.08-.65.08-.65a2.31 2.31 0 0 1 1.68 1.11a2.37 2.37 0 0 0 3.2.89a2.33 2.33 0 0 1 .7-1.44c-2.44-.27-5-1.19-5-5.32a4.15 4.15 0 0 1 1.11-2.91a3.78 3.78 0 0 1 .11-2.84s.93-.29 3 1.1a10.68 10.68 0 0 1 5.5 0c2.1-1.39 3-1.1 3-1.1a3.78 3.78 0 0 1 .11 2.84A4.15 4.15 0 0 1 19 11.2c0 4.14-2.58 5.05-5 5.32a2.5 2.5 0 0 1 .75 2v2.95c0 .35.2.63.75.52A10.8 10.8 0 0 0 23 11.77A10.89 10.89 0 0 0 12 1"/>
              </svg>
            </a>
            <a v-if="project.deploy" :href="project.deploy" target="_blank" rel="noopener noreferrer">
              <svg class="mt-3 ml-2" width="22" height="22" viewBox="0 0 512 512" xmlns="http://www.w3.org/2000/svg">
                <path fill="#000000" d="M432 320h-32a16 16 0 0 0-16 16v112H64V128h144a16 16 0 0 0 16-16V80a16 16 0 0 0-16-16H48a48 48 0 0 0-48 48v352a48 48 0 0 0 48 48h352a48 48 0 0 0 48-48V336a16 16 0 0 0-16-16ZM488 0H360c-21.37 0-32.05 25.91-17 41l35.73 35.73L135 320.37a24 24 0 0 0 0 34L157.67 377a24 24 0 0 0 34 0l243.61-243.68L471 169c15 15 41 4.5 41-17V24a24 24 0 0 0-24-24Z"/>
              </svg>
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
  
  <script>
  import CryptoSafe from '../assets/images/cryptosafe.jpeg';
  import Streetwear from '../assets/images/streetwear.jpeg';
  import Globo from '../assets/images/globo.jpeg';
  import RestoBrk from '../assets/images/restobrk.jpeg';
  import VideoRestoBrk from '../assets/videos/Resto-BRK.mp4';
  import VariableX from '../assets/images/variablex.jpeg';

  export default {
    name: 'ProjectGallery',
    data() {
      return {
        projects: [
          {
            name: 'Resto BRK',
            image: RestoBrk,
            description: 'Administrador de restaurante.',
            repo:'https://github.com/agucamejo/RestoBRK',
            deploy: VideoRestoBrk,
            technologies: [
                "C#",
                ".Net Core",
                "Boostrap5",
                "SQL Server",
            ]
          },
          {
            name: 'CryptoSafe',
            image: CryptoSafe,
            description: 'E-wallet de criptomonedas.',
            repo:'https://github.com/agucamejo/CryptoSaFe',
            deploy:'https://cryptosafearg.netlify.app/',
            technologies: [
                "Vue.js",
            ]
          },
          {
            name: 'La Variable X',
            image: VariableX,
            description: 'Landing page para centro educativo.',
            deploy:'https://lavariablex.com/',
            technologies: [
                "TypeScript",
                "TailwindCSS"
            ]
          },
          {
            name: 'Globo',
            image: Globo,
            description: 'Perfil de red social.',
            repo:'https://github.com/agucamejo/Globo',
            deploy:'https://globoo.vercel.app/',
            technologies: [
                "Vue.js",
            ]
          },
          {
            name: '1998-Streetwear',
            image: Streetwear,
            description: 'E-commerce de ropa urbana.',
            repo:'https://github.com/agucamejo/1998-Streetwear',
            deploy:'https://agucamejo.github.io/1998-Streetwear/',
            technologies: [
                "HTML",
                "CSS",
                "JavaScript"
            ]
          },
        ],
      };
    },
  };
  </script>
  
  <style scoped>

  .project-container{
    margin: 3rem auto;
    max-width: 70%;
  }

  svg{
    cursor: pointer;
  }
  
  .project-gallery-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
  }
  
  .project-card {
    position: relative;
    overflow: hidden;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    transition: box-shadow 0.3s ease;
    margin: 0rem 1.5rem 3rem 2rem;
  }
  
  .project-card:hover{
    box-shadow: 0 8px 12px rgba(0, 0, 0, 0.2);
  }

  .dark .project-card {
    position: relative;
    overflow: hidden;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(255, 255, 255, 0.1);
    transition: box-shadow 0.3s ease;
  }
  
  .dark .project-card:hover{
    box-shadow: 0 8px 12px rgba(255, 255, 255, 0.2);
  }

  .dark path{
    fill: #FFFFFF
  }

  .project-image {
    width: 100%;
    height: 180px; 
    object-fit: cover;
  }
  
  .project-details {
    padding: 16px;
  }

  @media (max-width: 768px) {
    .project-container{
      max-width: 100%;
      text-align: center;
    }

    .project-details div{
      justify-content: center;
    }
  }
  </style>
  