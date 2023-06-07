<template>
<div style="display:inline-block;float:left">
<label>search user by DOB <lablel>
<input type="text" v-model="searchDOB">
</div>
<div style="margin-left:20px;display:inline-block;float:left">
<label>search user by User Name <lablel>
<input type="text" v-model="searchUserName">
</div>

  <div class="hello" v-for="user in users" :key="user.userName">
    <div>User Name : {{ user.userName }}</div>
    <div>DOB : {{ user.DOB }}</div>
    <div>Profession : {{ user.Profession }}</div>
    <div>Salary : {{ user.salary }}</div>
    <div>ApplicationStatus: {{ user.ApplicationStatus }}</div>
  </div>
</template>

<script>
import userData from './users.json';
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  data() {
    return { 
      searchDOB:"",
      searchUserName:"",
      users: userData };
  },
  computed: {
    filteredDOB() {
      return this.users.filter(user=>user.DOB.toLowerCase().includes(this.searchDOB));
      
    },
    filteredUserName() {
      return this.users.filter(user=>user.userName.toLowerCase().includes(this.searchUserName));
    }

  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  margin: 30px 30px 10px 0;
  float: left;
  width: 300px;
  height: 200px;
  padding-top: 50px;
  border: 1px solid black;
}
</style>
