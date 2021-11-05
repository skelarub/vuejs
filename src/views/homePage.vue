<template>
  <div>
    <cRangeInput :startValue="startValue" :min="min" :max="max" :step="step" />
    <usersList v-if="bUsersList" />
    <userInfo v-else :id="user.id" :avatar="user.avatar" :first_name="user.first_name" :last_name="user.last_name" :email="user.email" />
  </div>
</template>

<script>
import cRangeInput from '../components/customRangeInput.vue';
import usersList from '../components/usersList.vue';
import userInfo from '../components/userInfo.vue';

export default {
  name: 'homePage',
  components: {
    cRangeInput,
    usersList,
    userInfo,
  },
  data: () => ({
    startValue: 15.5,
    min: 0,
    max: 100,
    step: .1,
    bUsersList: true,
    user: {},
  }),
}
</script>
