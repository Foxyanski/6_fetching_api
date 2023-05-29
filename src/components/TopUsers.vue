<template>
  <div class="main">
    <h1>Top Github Users</h1>
    <div class="user">
      <p>Name: {{ showUser.name }}</p>
      <p>Repos: {{ showUser.repos }}</p>
      <img :src="showUser.avatarUrl" />
    </div>
    <!-- <p>{{ users }}</p> -->
    <div class="buttons">
      <button @click="page++">Next</button>
      <button @click="page--">Back</button>
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'
import axios from 'axios'

const client_id = '94f0df1ee92c680d50ff'
const client_secret = '8aa837a61a7d0d7381709c44108a99a6f16b6aa1'
const user = 'foxyanski'
// const users = ref(null)
let page = ref(0)

const res = await axios.get(
  `https://api.github.com/users/${user}?client_id=${client_id}&client_secret=${client_secret}`
)
// users.value = res.data
watch(page, async () => {
  await axios.get(
    `https://api.github.com/users/${user}?client_id=${client_id}&client_secret=${client_secret}`
  )
})
const showUser = {
  name: res.data.name,
  repos: res.data.public_repos,
  avatarUrl: res.data.avatar_url
}
console.log(res.data)
</script>

<style scoped lang="scss">
.main {
  .user {
    img {
      width: 200px;
      height: 200px;
    }
  }
  .buttons {
    button {
      margin: 1rem;
    }
  }
}
</style>
