<template>
  <div id="app">
    <img :class="gender" :src="picture" :alt="firstName" />
    <h1>{{ firstName }} {{ lastName }}</h1>
    <h3>Email:{{ email }}</h3>
    <button v-on:click="getUser" :class="gender">Get Random User</button>
  </div>
</template>

<script>
//import HelloWorld from "./components/HelloWorld";

export default {
  name: "App",
  data() {
    return {
      firstName: "atharva",
      lastName: "sayankar",
      email: "atharva.sayankar@gmail.com",
      gender: "male",
      picture:
        "https://playuganda.com/wp-content/uploads/2020/12/profile-pic.jpg",
    };
  },
  methods: {
    async getUser() {
      const res = await fetch("https://randomuser.me/api");
      const { results } = await res.json();
      this.firstName = results[0].name.first;
      this.lastName = results[0].name.last;
      this.email = results[0].email;
      this.gender = results[0].gender;
      this.picture = results[0].picture.large;
      console.log(results);
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
img {
  height: 200px;
  border: 5px solid;
  border-radius: 50%;
  width: 200px;
}
.male {
  border-color: rgb(18, 6, 194);
  background-color: rgb(0, 0, 0);
  color: white;
}
.female {
  border-color: rgb(190, 105, 190);
  background-color: rgb(224, 140, 220);
  color: rgb(12, 8, 255);
}

button {
  cursor: pointer;
  display: inline-block;
  background: #333;
  color: white;
  font-size: 18px;
  border: 0;
  padding: 1rem 1.5rem;
}
</style>
