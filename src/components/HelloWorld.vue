<template>
<div style="display:inline-block;float:left">
<label>search user by DOB or User Name <lablel>
<input type="text" v-model="search">
</div>

  <div class="hello" v-for="(user,index) in userlist" :key="index">
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
      search:'',
      users: userData };
  },
  computed: {
    userlist() {
      for (let i = 0;i<this.users.length;i++) {
        if (this.users[i].DOB.toLowerCase().includes(this.search.trim().toLowerCase())) {
          return this.users.filter(user=>user.DOB.toLowerCase().includes(this.search.trim().toLowerCase()))
        }
        if (this.users[i].userName.toLowerCase().includes(this.search.trim().toLowerCase())) {
          return this.users.filter(user=>user.userName.toLowerCase().includes(this.search.trim().toLowerCase()));
        }
      }
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
