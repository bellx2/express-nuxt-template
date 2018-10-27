<template lang="pug"> 
  b-container
    b-row
      b-col
      b-col
        img.logo(src="~assets/img/logo.png" alt="Nuxt.js Logo")
        h1.title USERS(bootstrap)
        b-list-group
          b-list-group-item(:to="{ name: 'id', params: { id: index }}" v-for="(user, index) in users" :key="index")
            | {{ user.name }}
        p
      b-col
</template>

<script>
import axios from '~/plugins/axios'

export default {
  async asyncData () {
    let { data } = await axios.get('/api/users')
    return { users: data }
  },
  head () {
    return {
      title: 'Users'
    }
  }
}
</script>

<style scoped>
.title
{
  margin: 30px 0;
}
.users
{
  list-style: none;
  margin: 0;
  padding: 0;
}
.user
{
  margin: 10px 0;
}
</style>
