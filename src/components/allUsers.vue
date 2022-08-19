<template>
  <div>
        <div   v-for="person in users" :key="person[`id`]" >
            <h2>{{person[`avatar`]}}</h2>
            <p>{{person[`email`]}}</p>
        </div>

  </div>
</template>

<script>
import axios from "axios";
export default {
  mounted() {
    axios
      .request({
        url: `https://reqres.in/api/users`,
      })
      .then((response) => {
        this.users = response[`data`][`data`];
      })
      .catch((error) => {
        error;
      });
  },
  data() {
    return {
      users: []
    };
  },
};
</script>

<style scoped></style>
