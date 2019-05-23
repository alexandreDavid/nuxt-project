<template>
  <section class="container">
    <div>
      <logo />
      <h1>Create!</h1>
      <nuxt-link to="/" class="button--grey">Home page</nuxt-link>
    </div>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue'

export default {
  components: {
    Logo
  }
}
</script>
