<template>
  <div class="">
    <input type="text" placeholder="Enter first_name for searching" @input="onInput" v-model="textSearch">
    <table class="usersListTable">
      <tr>
        <th class="colID">id</th>
        <th class="colAvatar">avatar</th>
        <th class="colFN">first_name</th>
        <th class="colLN">last_name</th>
        <th class="colEml">email</th>
        <th><button v-if="!newRow" @click="rowAdd">PLUS</button></th>
      </tr>
      <tr v-if="newRow">
        <td></td>
        <td></td>
        <td><input type="text" v-model="first_name"></td>
        <td><input type="text" v-model="last_name"></td>
        <td><input type="text" v-model="email"></td>
        <td><button @click="insert">OK</button><button @click="cancel">Cancel</button></td>
      </tr>
      <tr v-for="(item, index) in filteredUsers" :key="index">
        <td>{{ index }}</td>
        <td><img :src="item.avatar" /></td>
        <td @click="getUserInfo(item)">{{ item.first_name }}</td>
        <td>{{ item.last_name }}</td>
        <td>{{ item.email }}</td>
        <td><button @click="rowDelete(index)">DEL</button></td>
      </tr>
    </table>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "usersList",
  data: () => ({
    url: 'https://reqres.in/api/users?page=1',
    users: [],
    first_name: '',
    last_name: '',
    email: '',
    textSearch: '',
    newRow: false,
  }),
  mounted() {
    this.getData();
  },
  methods: {
    getData() {
      axios.get( this.url )
      .then( response => {
        this.users = response.data.data;
      });
    },
    getUserInfo: function (item) {
      //console.log(item);
      this.$parent.user = item;
      this.$parent.bUsersList = false;
    },
    insert: function () {
      this.newRow = false;
      this.users.push({'first_name': this.first_name, 'last_name': this.last_name, 'email': this.email});
    },
    rowAdd: function () {
      this.newRow = true;
    },
    cancel: function () {
      this.newRow = false;
      this.first_name = '';
      this.last_name = '';
      this.email = '';
    },
    rowDelete: function (rowId) {
      this.users.splice(rowId, 1);
    }
  },
  computed: {
    filteredUsers() {
      let tempUsers = this.users;
      if (this.textSearch != '' && this.textSearch) {
        tempUsers = tempUsers.filter((item) => {
          return item.first_name
            .toUpperCase()
            .includes(this.textSearch.toUpperCase())
          })
        }
      return tempUsers;
    },
  }
}
</script>

<style>
  .usersListTable {
    width: 100%;
    text-align: left;
  }
</style>