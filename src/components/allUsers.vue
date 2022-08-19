<template>
  <div>
    <div v-for="person in user" :key="person[`id`]">
        <div v-if="user !== undefined">
            <h2>{{person[`avatar`]}}</h2>
            <p>{{person[`email`]}}</p>
        </div>
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
        for (let i = 0; i < response[`data`].length; i++) {
          this.user[`avatar`] = response[`data`][i][`avatar`];
          this.user[`email`] = response[`data`][i][`email`];
          this.user[`first_name`] = response[`data`][i][`first_name`];
          this.user[`id`] = response[`data`][i][`id`];
          this.user[`last_name`] = response[`data`][i][`last_name`];
        }
      })
      .catch((error) => {
        error;
      });
  },
  data() {
    return {
      user: {
        avatar: undefined,
        email: undefined,
        first_name: undefined,
        id: undefined,
        last_name: undefined,
      },
    };
  },
};
</script>

<style scoped></style>
