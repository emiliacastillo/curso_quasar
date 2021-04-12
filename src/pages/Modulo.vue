<template>

  <div class="q-pa-md q-gutter-sm">
   
    <q-page-sticky position="bottom-right" :offset="[18, 18]">
  <q-btn fab icon="add" color="accent" @click="prompt = true"/>
  </q-page-sticky>
    

     <div class="q-pa-md row items-start q-gutter-md">
      <q-card class="my-card">
      <q-card-section class="bg-primary text-white">
        <div class="text-h6">Our Changing Planet</div>
        <div class="text-subtitle2">by John Doe</div>
      </q-card-section>
      <q-separator />
      <q-card-actions align="right">
        <q-btn flat>Registrer</q-btn>       
      </q-card-actions>
    </q-card>
    </div>

    <q-dialog v-model="prompt" persistent>
      <q-card style="min-width: 350px">
        <q-card-section>
          <div class="text-h6">Add Module</div>
        </q-card-section>

        <q-card-section class="q-pt-none">
          <q-input color="blue" filled v-model="nombremodulo" placeholder="Module Name">
        <template v-if="nombremodulo" v-slot:append>
          <q-icon name="cancel" @click.stop="nombremodulo = null" class="cursor-pointer" />
        </template>
      </q-input>
       <q-input
      v-model="descripcion"
      filled
      type="textarea"  placeholder="Description"
    /> 
     <q-input color="blue" filled v-model="nota" placeholder="Qualification">
        <template v-if="nota" v-slot:append>
          <q-icon name="cancel" @click.stop="nota = null" class="cursor-pointer" />
        </template>
      </q-input>
       
        </q-card-section>

        <q-card-actions align="right" class="text-primary">
          <q-btn flat label="Cancel" v-close-popup />
          <q-btn flat label="Add module" v-close-popup @click="AddModule()" />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </div>
</template>
<script>
import { api } from 'boot/axios'
 import {id} from 'src/pages/Curso'
export default {
  data () {

    return {
      alert: false,
      confirm: false,
      prompt: false,
      nombremodulo: '',
      address: '',
      descripcion:'',
      nota:'',
      addmodule: null,
      
    }
  },
  methods:{
    AddModule(){
     
      api.post('/modulo',{nombre: this.nombremodulo,descripcion: this.descripcion,nota: this.nota,curso_Id:this.$route.params.idcurso }).then(response => (this.addmodule = response))
      .catch(error => console.log(error))
    
    }
  }
}
</script>