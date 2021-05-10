<template>
  <app-layout>
      <form @submit.prevent="submit">
          <div>
              <label for="name">Nome</label>
              <input type="text" id="name" v-model="user.name"/>
              <div v-show="errors.name">
                  {{ errors.name }}
              </div>
          </div>
          <div>
              <label for="email">E-mail</label>
              <input type="text" id="email" v-model="user.email"/>
              <div v-show="errors.email">
                  {{ errors.email }}
              </div>
          </div>
          <div>
              <label for="password">Senha</label>
              <input type="password" id="password" v-model="user.password"/>
              <div v-show="errors.email">
                  {{ errors.email }}
              </div>
          </div>
          <button>Editar</button>
      </form>
  </app-layout>
</template>

<script>
import AppLayout from '../../Layouts/AppLayout.vue'
export default {
    name: "Edit",
    components: {AppLayout},
    props:{
        user: Object,
        errors: Object
    },
    methods: {
        submit(){
            this.$inertia.put(`/users/${this.user.id}`, this.user);
        }
    }
}
</script>

<style>

</style>