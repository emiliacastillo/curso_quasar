<template>
  <q-page
    class="window-height window-width row justify-center items-center"
    style="background: linear-gradient(#8274C5, #5A4A9F);"
  >
    <div class="column q-pa-lg">
      <div class="row">
       <q-card square class="shadow-24" style="width:300px;height:485px;">
          <q-card-section class="bg-deep-purple-7">
            <h4 class="text-h5 text-white q-my-md">Create new account</h4>
            <div class="absolute-bottom-right q-pr-md" style="transform: translateY(50%);">
              <q-btn fab icon="close" color="purple-4" @click="$router.replace('/')" />
            </div>
          </q-card-section>
          <q-card-section>
            <q-form class="q-px-sm q-pt-xl q-pb-lg">
              <q-input square clearable v-model="email" type="email" label="Email">
                <template v-slot:prepend>
                  <q-icon name="email" />
                </template>
              </q-input>
              <q-input square clearable v-model="username" type="username" label="Username">
                <template v-slot:prepend>
                  <q-icon name="person" />
                </template>
              </q-input>
              <q-input square clearable v-model="password" type="password" label="Password">
                <template v-slot:prepend>
                  <q-icon name="lock" />
                </template>
              </q-input>
            </q-form>
          </q-card-section>
          <q-card-actions class="q-px-lg">
            <q-btn unelevated size="lg" color="purple-4" class="full-width text-white" label="Get Started" />
          </q-card-actions>
          <q-card-section class="text-center q-pa-sm">
            <p class="text-grey-6" @click="$router.replace('/signin')" >Return to login</p>
          </q-card-section>
        </q-card>
      </div>
    </div>    
  </q-page>
</template>


<script>
export default {
  name: 'Login',
  methods: {
    auth (network) {
      this.$hello(network).login({ scope: 'friends' })
        .then((res) => {
          console.log(res)
        })
    }
  },
  data () {
    return {
      email: '',
      username: '',
      password: ''
    }
  }
}
</script>

<style scoped>
.dark{
  background: #1817309a;
}
</style>
