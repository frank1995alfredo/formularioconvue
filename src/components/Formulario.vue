<template>
    <div class="container">
        <form>
          <div class="row">
              <div class="col-xs-12 col-md-6">
                 <h1>Formulario de Contacto</h1>
                 <hr>
                 <div class="form-group">
                     <label for="nombre">Nombre:</label>
                     <input type="text" id="nombre" class="form-control" v-model="datosPersona.nombre">
                 </div>
                 <div class="form-group">
                     <label for="email">Email:</label>
                     <input type="text" id="email" class="form-control" v-model="datosPersona.email">
                 </div>
                
              </div>
          </div>
          <div class="row">
            <div class="col-xs-12 col-md-6">
                     <label for="mensaje">Mensaje:</label><br>
                     <textarea id="mensaje" cols="60" rows="5" v-model="mensaje"></textarea>
                 </div>    
          </div>
          <div class="row">
              <div class="col-xs-12 col-sm-8 col-md-6">
                 <div class="form-group">
                    <label for="enviarmail">
                        <input type="checkbox" id="enviarmail" value="enviarmail" v-model="opcionMail">Enviar Email
                    </label>&nbsp; &nbsp;
                    <label for="enviarcopia">
                        <input type="checkbox" id="enviarcopia" value="enviarcopia" v-model="opcionMail">Enviar una copia
                    </label>
                 </div>
              </div>
          </div> 
          <div class="row">
              <div class="col-xs-12 col-sm-8 col-md-6">
                 <div class="form-group">
                    <label for="masculino">
                        <input type="radio" id="masculino" value="masculino" v-model="genero">Masculino
                    </label>&nbsp; &nbsp;
                    <label for="femenino">
                        <input type="radio" id="femenino" value="femenino" v-model="genero">Femenino
                    </label>
                 </div>
                 <div class="row">
                   <div class="col-xs-12 col-sm-8 col-md-8">
                      <label for="horario">Horario</label>
                      <select class="form-control" v-model="horario" id="horario">
                          <option v-for="item in datosHorario" :key="item" :selected="item == 'Manana'">{{ item }}</option>
                           
                      </select>
                   </div>
                 </div>
                 <br>
                   <div class="row">
                  <div class="col-xs-12 col-sm-8 col-md-6">
                      <button class="btn btn-primary" @click.prevent="enviar">Enviar datos</button>
                  </div>
              </div>
              </div>
          </div> 
          <br>
        </form> 
        <div class="row" v-if="enviado">
            <div class="col-xs-12 col-sm-6 col-md-6">
                <div class="panel panel-default">
                    <div class="panel panel-heading">
                       <h3>Datos Ingresados</h3>
                    </div>
                    <div class="panel-body">
                        <p>Nombre: {{ datosPersona.nombre }}</p>
                        <p>Correo: {{ datosPersona.email }}</p>
                        <p style="white-space: pre">Mensaje: <br> {{ mensaje }}</p>
                        <p>Opcion de envio:
                            <ul>
                                <li v-for="item in opcionMail" :key="item">{{ item }}</li>
                            </ul>
                        </p>
                        <p>Genero: {{ genero }}</p>
                        <p>Horario: {{ horario }}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'formulario',
    data(){
        return{
            datosPersona:{
               nombre: '',
               email: ''
            },
            mensaje: 'Test mensaje',
            opcionMail: [],
            genero: 'masculino',
            horario: 'Manana',
            datosHorario: ['Manana', 'Tarde', 'Noche'],
            enviado: false      
        }
    },
    methods: {
        enviar(){
            this.enviado = true;
        }
    }
}
</script>

