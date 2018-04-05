<template>
  <main class="hello">
    <div class="burger" @click="switchMenu">
      burger
    </div>
    <nav class="menu full" v-show="menuOpen">
      <menu-item pic="./assets/menuLogin.png" name="Profil" @changepage="changePage" :page="curPage"></menu-item>
      <menu-item pic="./assets/menuMap.png" name="Map" @changepage="changePage" :page="curPage"></menu-item>
      <menu-item pic="./assets/menuMap.png" name="Favori" @changepage="changePage" :page="curPage"></menu-item>
      <menu-item pic="./assets/menuMap.png" name="Parametres" @changepage="changePage" :page="curPage"></menu-item>
      <menu-item pic="./assets/menuMap.png" name="Deconnection" @changepage="changePage" :page="curPage"></menu-item>
    </nav>
    <div class="content">
      <div v-show="curPage === 'Profil'">
        <user></user>
      </div>
      <div v-show="curPage === 'Map'">
        <h2>Map</h2>
      </div>
    </div>
  </main>
</template>

<script>
/* eslint-disable */
import menuItem from './menuItem';
import user from './user';
import axios from 'axios';

export default {
  name: 'page',
  components: {menuItem, user},
  data () {
    return {
      curPage: "Profil",
      menuOpen: false,
    }
  },
  methods:{
    switchMenu(){
      this.menuOpen = !this.menuOpen;
    },
    changePage(page){
      this.menuOpen = false;
      this.curPage = page;
    },
    user(content){

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .burger
  {
    position: fixed;

    top: 2rem;
    left: 2rem;

    z-index: 1000;
  }
  .menu{
    // position: relative;


    display: flex;

    flex-flow: column;
    justify-content: stretch;
    align-items: flex-start;

    z-index: 500;
  }
</style>
