<template>
  <div id="app">
    <Home v-if="!isLogin"></Home>
    <Editor v-if="isLogin"></Editor>
  </div>
</template>

<script>
import Home from "./components/Home";
import Editor from "./components/Editor";
export default {
  name: "app",
  data:function() {
    return {
      isLogin: false
    };
  },
  created:function(){
firebase.auth().onAuthStateChanged(function(user) {
  console.log(user);
  if (user) {
    this.isLogin=true;
  } else {
    this.isLogin=false;
  }
});
  },
  components: {
    Home:Home,
    Editor:Editor
  },
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
