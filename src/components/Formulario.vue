<template>
  <section class="src-components-formulario">
    
    <div class="jumbotron">
       <h2>Formulario</h2>
      <hr>
      <hr>
      <br>

      <vue-form :state="formstate" @submit.prevent="enviar()">

        <!-- NOMBRE -->
        <validate tag="div">
          <label for="nombre">Nombre</label>
          <input type="text" 
          v-model.trim="formData.nombre" 
          required name="nombre" 
          autocomplete="off" 
          id="nombre" 
          class="form-control"
          :minlength="minCaracteres"
          :maxlength="maxCaracteres"/>

          <field-messages name="nombre" show="$dirty">
            <div slot="required" class="alert alert-warning">Este campo es requerido</div>
            <div slot="minlength" class="alert alert-warning">minimo{{minCaracteres}}caracteres</div>
            <div slot="maxlength" class="alert alert-warning">maximo{{maxCaracteres}}caracteres</div>
          </field-messages>
        </validate>
        <!-- Edad -->

        <validate tag="div">
          <label for="edad">Edad</label>
          <input type="number" 
          v-model="formData.edad" 
          required name="edad" 
          autocomplete="off" 
          id="edad" 
          class="form-control"
          :min="minEdad"
          :max="maxEdad"/>

          <field-messages name="edad" show="$dirty">
            <div slot="required" class="alert alert-warning">Este campo es requerido</div>
            <div slot="min" class="alert alert-warning">edad minima{{minEdad}}</div>
            <div slot="max" class="alert alert-warning">edad maxima{{maxEdad}}</div>
          </field-messages>
          </validate>

          <!-- Email -->
          <validate tag="div">
          <label for="email">Mail</label>
          <input type="email" 
          v-model="formData.mail" 
          required name="email" 
          autocomplete="off" 
          id="email" 
          class="form-control"
          />

          <field-messages name="email" show="$dirty">
            <div slot="required" class="alert alert-warning">Este campo es requerido</div>
            <div slot="email" class="alert alert-warning">Formato Mail invalido</div>
          </field-messages>
          </validate>

        <button class="btn btn-success my-4" :disabled="formstate.$invalid">Enviar</button>
      </vue-form>
     
      <!-- <pre>{{ formstate }}</pre> -->

    </div>
  </section>
</template>

<script>
export default {
  name: "src-components-formulario",
  props: [],
  mounted() {},
  data() {
    return {
      url:"https://6289095c7af826e39e6800fe.mockapi.io/posts",
      formstate:{},
      formData: this.getInicialData(),
      maxCaracteres:15,
      minCaracteres:3,
      maxEdad:120,
      minEdad:18,
      usuario:[],
    };
  },
  methods: {
    getInicialData(){
      return{
        nombre:null,
        edad:null,
        mail:null,
      }
    },
    enviar(){
      this.postUsuario() 
      this.formData = this.getInicialData();
      this.formstate._reset()
    },
    async postUsuario() {
        let usuarioNew = {
          nombre: this.formData.nombre,
          edad: this.formData.edad,
          email: this.formData.mail,
        }

        try {
          let { data: posts } = await this.axios.post(this.url, usuarioNew, {'content-type' : 'application/json'})
          console.log('AXIOS POST usuario', posts)

        }
        catch(error) {
          console.error('Error en postUsuario()', error.message)
        }    
      },
      getUsuarios(){
        console.log("usuario")
      }
  },
  computed: {

  },
};
</script>

<style scoped lang="css">
.src-components-formulario {
}
h2 {
    color: black;    
  }
hr {
  background-color: #ddd;
}

</style>
