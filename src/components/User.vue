<template>
   <div className="user">
    <button @click="deleteUser(index)">Delete</button>
  <h3>{{ user.name }}</h3>
  <p>{{ user.email }} - <b>{{ user.pass }}</b></p>
 </div>
</template>

<script>
export default {
    props: {
        user: {
            type: Object,
            required: true
        },
        index: {
            type: Number,
            required: true
        },
        deleteUser: {
            type: Function,
            required: true
        }
    }
}
</script>

<style scoped>
button {
  border-radius: 5px;
  border: 1px solid black;
  outline: none;
  padding: 10 px 20 px;
  background: rgb(230, 87, 87);
  color:rgb(71, 2, 2);
  font-weight: bolder;
  cursor:pointer;
  transition: transform 500ms ease;
  float: right;
}
</style>