<template>
  <div class="container">
    <div class="row">
      <div class="col-sm-2">
        <div class="participantes">
          Participantes: <span style="color: white;"> {{participantes}} </span>
        </div>
        <div v-if="participantes >= 5" class="card ganador" >
          <img src="data:image/jpeg;base64,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" 
            class="card-img-top ganador-imagen" alt="...">
          <div class="card-body card-body-ganador">
            <h5>Ganador</h5>
            <p class="card-text">
              {{ganador.nombre}} {{ganador.apellido}} <br>
              {{ganador.correo}} <br>
              {{ganador.ciudad}}

            </p>
          </div>

          
        </div>

        
          <a class="btn btn-outline-success " :href="url+'/clientes/export'">Descargar Registros</a>          
          <!-- <a href="http://localhost:8000/api/clientes/export">Descargar</a> -->
        

        
       
      </div>
      <div class="col-sm-8">
        <div class="card">
          <h2 class="blanco">Registro</h2>
          <div class="form">

            <form id="loginForm" @submit="registrarUsuario">
              <div class="row">
                <div class="col-sm-6">
                  <div class="mb-3">
                    <input
                      type="text"
                      class="form-control"
                      id="name"                      
                      aria-describedby="emailHelp"
                      placeholder="Nombre"
                      required
                      pattern="[A-Za-z]+"
                      title="Solo se aceptan letras"
                      v-model="usuario.nombre"
                    />
                  </div>

                  <div class="mb-3">
                    <input
                      type="number"
                      class="form-control"
                      id="cedula"
                      placeholder="Cedula"
                      required
                      v-model="usuario.cedula"
                    />
                  </div>

                  <div class="mb-3">
                    <select
                      class="form-select"
                      aria-label="Default select example"
                      v-model="usuario.ciudad"
                    >
                      <option selected disabled>Ciudad</option>
                      <option v-for="municipio,key in municipios" :key="key" :value="municipio.nombre">{{municipio.nombre}}</option>
                      
                    </select>
                  </div>

                  <div class="mb-3">
                    <input
                      type="email"
                      class="form-control"
                      id="email"
                      placeholder="Correo"
                      required
                      v-model="usuario.correo"
                    />
                  </div>
                </div>
                <div class="col-sm-6">
                  <div class="mb-3">
                    <input
                      type="text"
                      class="form-control"
                      id="lastname"
                      placeholder="Apellido"
                      required
                      v-model="usuario.apellido"
                      pattern="[A-Za-z]+"
                      title="Solo se aceptan letras"
                    />
                  </div>

                  <div class="mb-3">
                    <select @change="cambioDepartamento"
                      class="form-select"
                      aria-label="Default select example"
                      v-model="usuario.departamento"                      
                    >
                      <option selected disabled >Departamento</option>
                      <option v-for="departamento, key in departamentos" :key="key" :value="departamento">{{departamento.nombre}}</option>
                     
                    </select>
                  </div>

                  <div class="mb-3">
                    <input
                      type="number"
                      class="form-control"
                      id="celular"
                      placeholder="Celular"
                      required
                      v-model="usuario.celular"
                    />
                  </div>

                  <div class="form-check">
                  <input
                    class="form-check-input"
                    type="checkbox"
                    value=""
                    id="flexCheckDefault"
                    v-model="usuario.autorizacion"
                  />
                  <label class="form-check-label" for="flexCheckDefault">
                    Autorizo el <a href="https://www.sic.gov.co/manejo-de-informacion-personal" target="_blanck">tratamiento de mis datos</a> 
                  </label>
                </div>
                </div>
              </div>

              
              <button type="submit" class="btn btn-primary form-control">
                Guardar
              </button>
            </form>
          </div>
        </div>
      </div>
      <div class="col-sm-2"></div>
    </div>
  </div>
</template>

<script>
import { ref } from '@vue/reactivity';
export default {


  setup() {

      const url = 'http://localhost:8000/api';
      const usuario = ref({});
      const departamentos = ref([]);
      const municipios = ref([]);
      const participantes = ref(0);
      const ganador = ref({});

      const cantidadaParticipantes = async () => {
        try {
          
          const res = await fetch(url+'/cliente');
          const datos = await res.json();
          participantes.value = datos.res;
          ganador.value = datos.ganador;          
          
        } catch (error) {
          console.log(error)
        }
      }
      cantidadaParticipantes();

      const cambioDepartamento = async () => {
        

        try {
            const res = await fetch(url+'/municipio/'+usuario.value.departamento.id);
            const datos = await res.json();
            municipios.value = datos.res;            
            
        } catch (error) {
          console.log(error)
        }
      }

      const cargarDepartamentos = async () => {

          try {
              
              const res = await fetch(url+'/departamento');
              const datos = await res.json();
              departamentos.value = datos.departamentos;
              

          } catch (error) {
              console.log(error)
          }
      }
      cargarDepartamentos();

           


      const registrarUsuario = async (e) => {
          e.preventDefault();
          
          if(!usuario.value.departamento || !usuario.value.ciudad){
            return swal("Todos los campos son obligatorios!", "Eliga Departamento y Municipio", "info");
          }
          if(!usuario.value.autorizacion){
            return swal("Terminos!", "Debe aceptar los terminos", "info");
          }
                 

          try {
              
              const res = await fetch(url+'/cliente',{
                  method:'POST',
                  body:JSON.stringify(usuario.value),
                    mode:'cors',
                    headers:{
                        'Content-Type':'application/json'
                    }
              });
              const datos = await res.json();
              
              if(datos.status){
                swal("Bienvenido a participar!", "Usuarios registrado con exito.", "success");
                usuario.value = {};
                cantidadaParticipantes();
              }

          } catch (error) {
              console.log(error)
          }

      }





      return {
          registrarUsuario, usuario, municipios, departamentos,
          cambioDepartamento, participantes, ganador, url
      }

  },
};
</script>


<style>
.card {
  display: flex;
  justify-content: center;
  width: 30rem;
  margin-top: -10vh;
  background-color: rgb(59, 61, 68);
}

.form {
  padding: 20px;
}

.blanco {
  color: whitesmoke;
}

.link-registro {
  padding-top: 5vh;
}

.link-registro a {
  color: rgb(138, 180, 167);
}

.link-registro a:hover {
  color: rgb(93, 111, 133);
}

.bi {
  padding-left: 10px;
}

span {
  color: whitesmoke;
}

.form-text {
  color: rgb(161, 76, 143);
}

h2 {
  text-align: center;
}

.form-check-label {
    color: whitesmoke;
}

.participantes {
  color: white;
  margin-left: -30vw;
  margin-top: -20vh;
  font-family: "Lato", cursive;
  font-size: 32px;
  color: orange;
  font-weight: bolder;
}

.ganador {
  width: 20vw;
  margin-top: 10vh;
  margin-left: -20vw;
}

.ganador-imagen {
  padding: 10px;  
  border-radius: 50px;
}

h5 {
  color: rgb(172, 114, 8);
  font-size: 30px;
}

.card-body-ganador p{
  text-align: left;
  color: rgb(210, 228, 222);
  font-size: 17px;
}

.btn-outline-success {
  margin-top: 5vh;
  margin-left: -28vw;
}

</style>