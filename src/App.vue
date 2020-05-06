<template>
  <div id="app">
    <h3>{{ titulo }}</h3>
    <div class="form">
      <div class="form-group">
        <label>Título</label>
        <input class="form-control" type="text" v-model="nota.titulo">
      </div>
      <div class="form-group">
        <label>Texto</label>
        <textarea v-model="nota.texto" class="form-control"></textarea>
      </div>
      <button class="btn btn-primary" @click="agregarNota">
        Enviar
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      titulo: 'Gestión de Notas',
      nota: {
        titulo: '',
        texto: ''
      },
      notas:[
        {
          titulo: 'Ir al cine',
          texto: 'Examinar las peliculas de estreno',
          fecha: new Date(Date.now()).toTimeString()
        }
      ]
    }
  },
  methods: {
    agregarNota: function() {
      let { texto, titulo} = this.nota;
      this.notas.push({
        titulo,
        texto,
        fecha: new Date(Date.now()).toTimeString()
      })
    }
  }
}
</script>

<style>
  .form {
    text-align: left;
  }
</style>
