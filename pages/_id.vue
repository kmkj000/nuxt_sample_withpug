<template lang="pug">
  section.container
    img(:src="`https://github.com/${user.login}.png`" :alt="user.name")
    h1 {{user.name}}
</template>

<script>
import axios from 'axios'

export default {
  async asyncData ({ params }) {
    const { data: user } = await axios.get(`https://api.github.com/users/${params.id}`)
    return {
      user,
      test: 0
    }
  }
}
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  flex-direction: column;
}

.container img{
  margin-bottom: 20px;
  border-radius: 50%;
  overflow: hidden;
}
</style>
