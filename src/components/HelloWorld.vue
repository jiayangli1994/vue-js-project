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
    <button v-on:click="edit(index)" style="margin-top:20px">Edit details</button>
  </div>

  <div div v-if="show" class="modal-mask">
    <div>User Name : {{ users[this.indexValue].userName }}</div>
    <div>DOB : {{ users[this.indexValue].DOB }}</div>
    <div>Profession : {{users[this.indexValue].Profession }}</div>
    <div>Salary : {{ users[this.indexValue].salary }}</div>
    <div>ApplicationStatus: {{ users[this.indexValue].ApplicationStatus }}</div>
    <select v-model="selected">
        <option v-for="option in options" :value="option.status">
        {{ option.status }}
        </option>
    </select>
    <button v-on:click="close()" style="margin-top:20px">Save details</button>
    <button v-on:click="save()" style="margin-top:20px">Close</button>

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
      show: false,
      indexValue: 0,
      selected:'',
      options: [{status:'Processed'},{status:'Pending'},{status:'Declined'}],
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

  },
  methods : {
    edit(index) {
      this.show = true;
      this.indexValue = index;

    },
    close() {
      this.show = false;
    },
    save() {
      this.show = false;
      users[this.indexValue].ApplicationStatus = selected;
      selected = '';
      this.indexValue= 0;
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
