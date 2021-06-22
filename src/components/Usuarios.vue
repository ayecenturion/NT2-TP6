<template>

  <section class="src-components-usuarios">
    <div class="jumbotron">
      <h1>Usuarios</h1>
      <hr>
        
      <button class="btb btn-light m-3"  @click="getUsuarios">Mostrar Usuarios</button>  

      <div v-if="usuarios.length" class="table">
        <table class="table table-light">
          <tr>
            <th v-for="(col, index) in getCols" :key="index">{{col}}</th>
          </tr>

          <tr v-for="(usuario, index) in usuarios" :key="index">
            <td v-for="(col, index) in getCols" :key="index">{{usuario[col]}}</td>
          </tr>
        </table>
      </div>
      <h4 v-else class="alert alert-danger"> No hay Usuarios por mostrar </h4>
    </div>
  </section>

</template>

<script lang="js">

  export default  {
    name: 'src-components-usuarios',
    props: [],
    mounted () {

    },
    data () {
      return {
        url: 'https://609dbec433eed8001795709d.mockapi.io/usuarios2',
        usuarios: []
      }
    },
    methods: {
      getUsuarios(){
        this.axios(this.url)
        .then(respuesta => {this.usuarios = respuesta.data
        })
        .catch(error => console.error(error))
      }
      
    },
    computed: {
      getCols(){
        return Object.keys(this.usuarios[0])
      }
    }
}


</script>

<style scoped lang="css">
  .src-components-usuarios {

  }
</style>
