<template>
  <div class="container">
    <!-- <p>{{ users[0].id }}, {{ users[0].name }}</p> -->
    <hr />
    <ul>
      <li v-for="user in users" :key="user.id">
        {{ user.id }}, {{ user.name }}
      </li>
    </ul>
  </div>
</template>

<script>
const axios = require("axios");
let url = "https://jsonplaceholder.typicode.com/users/";
// let url = "https://jsonplaceholder.typicode.com/users/xxx";
export default {
  asyncData({ params, error }) {
    return axios
      .get(url)
      .then((res) => {
        return { users: res.data };
      })
      .catch((err) => {
        console.error(err);
        error({ users: err.response.status, message: "Error" });
      });
  },
};
</script>