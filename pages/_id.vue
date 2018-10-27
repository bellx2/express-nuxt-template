<template lang="pug">
  b-container
    b-row
      b-col
      b-col
        img.logo(src="~assets/img/logo.png" alt="Nuxt.js Logo")
        b-jumbotron(lead="User" :header = "user.name")
        p
        b-button(to="/") Back to Users
        p
      b-col
</template>

<script>
import axios from '~/plugins/axios'

export default {
  name: 'id',
  asyncData ({ params, error }) {
    return axios.get('/api/users/' + params.id)
      .then((res) => {
        return { user: res.data }
      })
      .catch((e) => {
        error({ statusCode: 404, message: 'User not found' })
      })
  },
  head () {
    return {
      title: `User: ${this.user.name}`
    }
  }
}
</script>

<style scoped>
.title
{
  margin-top: 30px;
}
.info
{
  font-weight: 300;
  color: #9aabb1;
  margin: 0;
  margin-top: 10px;
}
.button
{
  margin-top: 30px;
}
</style>
