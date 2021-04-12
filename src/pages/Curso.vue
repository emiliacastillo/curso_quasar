<template>
  <div class="column no-wrap flex-center">
    <div class="q-gutter-y-md column" style="max-width: 300px">
     
      <q-input color="blue" filled v-model="nombrecurso" placeholder="Course Name">
        <template v-if="nombrecurso" v-slot:append>
          <q-icon name="cancel" @click.stop="nombrecurso = null" class="cursor-pointer" />
        </template>
      </q-input>
      
            
    <q-input
      v-model="descripcion"
      filled
      type="textarea"  placeholder="Description"
    /> 
    <q-input color="blue" filled v-model="qualification" placeholder="Qualification">
        <template v-if="qualification" v-slot:append>
          <q-icon name="cancel" @click.stop="qualification = null" class="cursor-pointer" />
        </template>
      </q-input>  
       <q-input color="blue" filled v-model="price" placeholder="Price">
        <template v-if="price" v-slot:append>
          <q-icon name="cancel" @click.stop="price = null" class="cursor-pointer" />
        </template>
      </q-input> 
  
     <div class="q-gutter-y-md column" style="max-width: 300px">
     Registration date
    </div>  
   

    <q-date v-model="registrationdate" registrationdate range/>
  </div>
    <div class="q-gutter-y-md column" style="max-width: 300px">
   <q-btn
      :loading="loading2"
      :percentage="percentage2"
      round
      color="secondary"
      @click="startComputing(2)"
      icon="cloud_upload"
    />
    
    </div>
  </div>
   
      </template>
     
  <script>
  import { api } from 'boot/axios'
export default {
  data () {
    return {
      descripcion: '',
       nombrecurso: '',
       qualification: '',
      registrationdate: { from: '2020/07/08', to: '2020/07/17' },
      price: '',
      loading2: false,
      percentage2: 0,
      addcurso: null,
     
    }
    
  },
  methods: {
    startComputing (id) {
      this[`loading${id}`] = true
      this[`percentage${id}`] = 0
      this[`interval${id}`] = setInterval(() => {
        this[`percentage${id}`] += Math.floor(Math.random() * 8 + 10)
        if (this[`percentage${id}`] >= 100) {
          clearInterval(this[`interval${id}`])
          this[`loading${id}`] = false
        }
      }, 700)
     
     
     api.post('/curso',{nombre: this.nombrecurso,nota: this.qualification,precio:this.price, descripcion: this.descripcion,fecha_inicio_incripcion:this.registrationdate.from, fecha_fin_incripcion:this.registrationdate.to}).then(response => (this.addcurso = response))
      .catch(error => console.log(error))
      .finally(() =>this.$router.push({

                  path: "/modulo/"+this.addcurso.data.id,
                 params:{
                 idcurso: this.addcurso.data.id,
                }
                }))
     
   
    }
  },

  beforeDestroy () {
    
    clearInterval(this.interval2)
  }
}
</script>