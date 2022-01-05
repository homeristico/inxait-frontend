<template>
  <div class="snap-container">
    
    <div v-for="section,key in sections" :key="key"
       class="snap-section snap-section-imagen" 
      :style="'background-image: url('+section.url+');'"
       >
       <div class="contenido">
        <h3>{{section.title}}</h3>
        <p>{{section.content}}</p>
       </div>
    </div>   

    <!-- Formulario participación sorteo -->
    <div 
       class="snap-section snap-section-imagen formulario"        
       >
        <Formulario></Formulario>
    </div>  


  </div>

  <!-- <img :src="url" alt=""> -->
</template>

<script>
import { ref } from "@vue/reactivity";
import Formulario from './components/Formulario.vue';

export default {
  name: "App",
  components: {
    Formulario
  },
  setup() {
    
    let sections = ref([]);

    const cargar = () => {
      sections = [
        {
          title: "Concursa",
          content:
            "Participa en el concurso que sera realizado como parte de la promoción de la marca.",
          url:'https://memolira.com/wp-content/uploads/2020/10/SSC-Tuatara-el-auto-mas-veloz-de-la-historia.jpg'
        },
        {
          title: "Participa",
          content:
            "Para participar, debes registrarte completando todos los campos requeridos.",
          url:'https://www.mitsubishi-motors.com.pe/blog/wp-content/uploads/2020/06/hatchbak-new-mirage-mitsubishi.jpg'
        },
        {
          title: "Sorteo",
          content:
            "Una vez se hayan registrado por lo menos 5 personas, se realizara el sorteo.",
          url:'https://arc-anglerfish-arc2-prod-infobae.s3.amazonaws.com/public/4GSUPRZXXREO7A3YKFIT3W2RMM.jpg'
        }
      ];
    };
    cargar();

    return {
      sections, 
    };
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

.snap-container {
  height: 100vh;
  overflow: auto;
  scroll-snap-type: y mandatory;
}

.snap-section {
  text-align: center;
  padding: 200px 300px 0 300px;
  scroll-snap-align: start;
  min-height: 100%;
  /* min-height: 70vh; */
}

.snap-section h3 {
  font-family: "Lato", cursive;
  font-size: 62px;
  color: orange;
  font-weight: bolder;
  margin-bottom: 30px;  
}

p {
  font-family: "Lato", cursive;
  font-size: 22px;
  color: white;
  font-weight: 500;    
  text-align: justify;
}

.contenido {
  max-width: 30vw;
  margin-left: -20vw;
  margin-top: -10vh;
}

.snap-section-imagen {
   background-position: center;
   background-repeat: no-repeat; 
   background-size: cover;
}

.formulario {
  background-image: linear-gradient(to bottom right, rgba(11, 15, 17, 0.972), rgb(4, 24, 29));
}


</style>
