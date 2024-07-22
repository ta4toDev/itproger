<template>
  <input type="text" v-model="userName" placeholder="Name">
  <input type="password" v-model="userPass" placeholder="Password">
  <input type="email" v-model="userEmail" placeholder="Email">
  <p className="error">{{ error }}</p>
 <button @click ="sendData()">Senden</button>

  <div v-if="users.length == 0" className ="user">No Users</div>
  <div v-else-if="users.length == 1" className ="user">Users has 1 element</div>
  <div v-else className ="user">Users has more than 1 element</div>

 <User v-for="(el, index) in users" :key="index" :user="el" :index="index" :deleteUser="deleteUser" />

</template>


<script>
import User from './components/User.vue';

export default {
  components: { User },
  data() {
    return {
      users: [],
      error: '',
      userName:'',
      userPass: '',
      userEmail: ''
    }
  },
  methods: {
    sendData() {
      if(this.userName == '') {
        this.error = 'Enter a name';
        return;
      } else if(this.userEmail == '') {
        this.error = 'Enter a email';
        return;
      } else if (this.userPass == '') {
        this.error = 'Enter a password';
        return;
      }

      this.error = '';

      this.users.push({
          name: this.userName,
          pass: this.userPass,
          email: this.userEmail
        })
    },
    deleteUser(index) {
      this.users.splice(index, 1);
    }
  }
}
</script>

<style scoped>
input {
  display: block;
  margin-bottom: 10px;
  border-radius: 3px;
  border: 1px solid rgb(175, 168, 168);
  outline: none;
  padding: 10 px 15 px;
  background: #fafafa;
  color:rgb(6, 6, 6);
}
button {
  border-radius: 5px;
  border: 1px solid black;
  outline: none;
  padding: 10 px 20 px;
  background: silver;
  color:gray;
  font-weight: bolder;
  cursor:pointer;
  transition: transform 500ms ease;
}
button:hover {
  transform: translateY(-5x);
}
.user {
  width: 500px;
  margin-top: 20px;
  border: 1px solid silver;
  background: #fdc9c9;
  color:black;
  padding: 20px;
  border-radius: 5px;
}
</style>
