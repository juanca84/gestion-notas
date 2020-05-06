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
    <div class="col-sm-12">
      <div class="col-sm-4 nota" v-for="nota in notas">
        <div class="card">
          <div class="card-block">
            <div class="card-title">
              {{nota.titulo}}
            </div>
            <div class="card-subtitle mb-2 text-muted">
              {{nota.fecha}}
            </div>
            <div class="card-text">
              {{nota.texto}}
            </div>
          </div>
        </div>
      </div>
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
        texto: texto,
        titulo: titulo,
        fecha: new Date(Date.now()).toLocaleString()
      })
    }
  }
}
</script>

<style>
  .form {
    text-align: left;
  }
  .card {
    text-align: left;
    border: 1px solid #2c3e50;
    border-radius: 4px;
    padding-left: 8px;
    padding-right: 8px;
  }
  .nota {
    padding: 5px;
  }
</style>
