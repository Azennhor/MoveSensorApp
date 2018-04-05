<template>
  <main class="hello">

    <div class="menu">
      <menu-item pic="./assets/menuLogin.png" name="login" @changepage="changePage" :page="curPage"></menu-item>
      <menu-item pic="./assets/menuLogin.png" name="map" @changepage="changePage" :page="curPage"></menu-item>
    </div>
    <div class="content">
      <div v-show="curPage === 'login'">
        <!-- <h2>Login</h2> -->
        <user></user>
      </div>
      <div v-show="curPage === 'map'">
        <h2>Map</h2>
      </div>
    </div>
  </main>
</template>

<script>
/* eslint-disable */
import menuItem from './menuItem';
import user from './user';
// import axios from 'axios';

export default {
  name: 'page',
  components: {menuItem, user},
  data () {
    return {
      curPage: "login"
    }
  },
  methods:{
    changePage(page){
      this.curPage = page;
      // console.log(page);      
    },
    user(content){

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
