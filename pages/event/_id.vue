<template>
  <div class="user">
    <h3>{{ name }}</h3>
    <h4>@{{ username }}</h4>
    <p>Email : {{ email }}</p>
    <p>
      <NuxtLink to="/">
        List of users
      </NuxtLink>
    </p>
  </div>
</template>

<script>
export default {
  validate({ params }) {
    return !isNaN(+params.id)
  },
  async asyncData({ params, error, $axios }) {
    try {
      const { data } = await $axios.get(
        `https://jsonplaceholder.typicode.com/posts/${+params.id}`
      )
      return data
    } catch (e) {
      error({ message: 'User not found', statusCode: 404 })
    }
  }
}
</script>

<style scoped>
.user {
  text-align: center;
  margin-top: 100px;
  font-family: sans-serif;
}
</style>
