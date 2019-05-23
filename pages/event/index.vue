<template>
  <section class="container">
    <div>
      <logo />
      <h1 class="title">
        nuxt-project
      </h1>
      <h2 class="subtitle">
        My prime Nuxt.js project
      </h2>
      <nuxt-link to="/" class="button--grey">Home</nuxt-link>
      <h2>Users</h2>
      <ul class="users">
        <li v-for="user in users" :key="user.id">
          <NuxtLink :to="'/users/' + user.id">
            {{ user.name }}
          </NuxtLink>
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue'

export default {
  components: {
    Logo
  },
  async asyncData({ $axios }) {
    const { data } = await $axios.get(
      'https://jsonplaceholder.typicode.com/users'
    )
    return { users: data }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
