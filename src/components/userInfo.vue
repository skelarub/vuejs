<template>
  <div class="">
    <a class="userinfo" @click="clickLink">Назад</a>
    <div class="userinfo">
      <span>{{ id }}</span>
      <span><img :src="avatar" /></span>
      <span>{{ first_name }}</span>
      <span>{{ last_name }}</span>
      <span>{{ email }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'userInfo',
  props: {
    id: {
      type: Number,
      default: 0,
    },
    avatar: {
      type: String,
      default: '',
    },
    first_name: {
      type: String,
      default: '',
    },
    last_name: {
      type: String,
      default: '',
    },
    email: {
      type: String,
      default: '',
    }
  },
  methods: {
    clickLink: function () {
      this.$parent.bUsersList = true;
      this.$parent.user = '';
    }
  },
}
</script>

<style>
  a.userinfo {
    cursor: pointer;
  }
  .userinfo span {
    display:block;
    padding: 1rem;
  }
  div.userinfo {
    display: flex;
    justify-content: center;
  }
</style>