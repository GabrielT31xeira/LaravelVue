<template>
  <app-layout>
      <div>
          <h1>Usuarios</h1>
          <inertia-link :href="route('users.create')">Cadastrar</inertia-link>
      </div>
      <table>
          <thead>
              <th>Nome</th>
              <th>E-mail</th>
              <th>Ações</th>
          </thead>
          <tbody>
              <tr v-for="user in users" :key="user.id">
                  <td>{{ user.name }}</td>
                  <td>{{ user.email }}</td>
                  <td>
                      <inertia-link :href="route('users.edit',user.id)">Editar</inertia-link>
                      <button type="button" @click="excluir(user.id)">Delete</button>
                  </td>
              </tr>
          </tbody>
      </table>
  </app-layout>
</template>

<script>
import AppLayout from '../../Layouts/AppLayout.vue'
export default {
    name: 'Index',
    components: {AppLayout},
    props: {
        users: Array
    },
    methods: {
        excluir(id) {
            this.$inertia.delete(`/users/${id}`);
        }
    }
}
</script>

<style>

</style>
