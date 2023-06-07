<template>
  <button>hi</button>
  <div class="hello" v-for="(user, index) in userlist" :key="index">
    <div>User Name : {{ user.userName }}</div>
    <div>DOB : {{ user.DOB }}</div>
    <div>Profession : {{ user.Profession }}</div>
    <div>Salary : {{ user.salary }}</div>
    <div>ApplicationStatus: {{ user.ApplicationStatus }}</div>
    <button>hi</button>
  </div>
</template>

<script>
import userData from './users.json';
export default {
  name: 'popup',
  props: {
    msg: String,
  },
  data() {
    return {
      search: '',
      show: false;
      users: userData,
    };
  },
  computed: {},
  methods: {
    edit: function (event){
      this.show = true;
      console.log(hi);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
