<template>
  <div class="q-pa-md">
     <q-page-container>
        <q-page padding>
         
  <div class="q-pa-md">
    

    <q-carousel
      v-model="slide"
      swipeable
      animated
      :navigation-position="navPos"
      navigation
      padding
      height="200px"
      class="bg-purple text-white rounded-borders"
    >
      <q-carousel-slide name="style" class="column no-wrap flex-center">
        <q-icon name="assignment" size="36px" />
        <div class="q-mt-md text-center">
          <p>All courses</p>
        </div>
      </q-carousel-slide>
      <q-carousel-slide name="tv" class="column no-wrap flex-center">
        <q-icon name="assignment_ind" size="36px" />
        <div class="q-mt-md text-center">
          <p>My courses</p>
        </div>
      </q-carousel-slide>
      <q-carousel-slide name="layers" class="column no-wrap flex-center">
        <q-icon name="school" size="36px" />
        <div class="q-mt-md text-center">
          <p> My approved courses </p>
        </div>
      </q-carousel-slide>
      <q-carousel-slide name="map" class="column no-wrap flex-center">
        <q-icon name="handyman" size="36px" />
        <div class="q-mt-md text-center">
          <p>Config my acount</p>
        </div>
      </q-carousel-slide>
    </q-carousel>
  </div>
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
     <q-page-sticky position="bottom-right" :offset="[18, 18]">
  <q-btn fab icon="add" color="accent" @click="AddCurso()"/>
  </q-page-sticky>
        </q-page>
        
      </q-page-container>
   
  </div>
  
</template>
  
 
   <script>
export default {
  data () {
    return {
         navPos: 'bottom',     
         slide: 'style',
     
    }
     },
     methods:{
       AddCurso(){

       this.$router.push('/curso')

       }
       
     }
}
</script> 

<style lang="sass" scoped>
.my-card
  width: 100%
  max-width: 250px
</style>