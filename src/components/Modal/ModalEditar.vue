<template>
  <div>
    <v-dialog
      v-model="dialog"
      persistent
      max-width="290"
    >
      
      <v-card>
        <v-card-title class="text-h5">
          Editar
        </v-card-title>
        <v-text-field
          class="px-3"
          label="Título"
          placeholder="Informe o novo título"
          outlined
          v-model="titulo"
        ></v-text-field>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="gray"
            text
            @click="$emit('fechaModal')"
          >
            Cancelar
          </v-btn>
          <v-btn
            color="green darken-1"
            text
            @click="handleEditar()"
          >
            Salvar
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
  export default {
    props:[
      'tarefa'
    ],
    data () {
      return {
        dialog: true,
        titulo: null
      }
    },
    created(){
      this.titulo = this.tarefa.titulo
    },
    methods:{
      handleEditar(){
        let novaTarefa = {
          titulo: this.titulo,
          id: this.tarefa.id
        }
        this.$store.commit('editarTarefa', novaTarefa)
        this.$emit('fechaModal')
      }
    }
  }
</script>

<style>

</style>