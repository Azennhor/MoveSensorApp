<template>
  <div>
    <div v-if="mode === 'choose'">
      <!-- <img src="./assets/logIcon.png" alt=""> -->
      <button @click="toConnect">se connecter</button>
      <button @click="toSign">s'enregistrer</button>      
    </div>    
    <div v-if="mode === 'login'">
      <input type="text" name="login" placeholder="nom d'utilisateur" v-mode="user">
      <input type="password" name="passw" placeholder="mot de passe" v-mode="pass">
      <button @click="connect">se connecter</button>
      <button @click="back">retour</button>
    </div>
    <div v-if="mode === 'sign'">
      <input type="text" name="login" placeholder="nom d'utilisateur" v-mode="user">
      <input type="password" name="passw" placeholder="mot de passe" v-mode="pass">
      <button @click="sign">s'enregistrer</button>
      <button @click="back">retour</button>
    </div>
  </div>
</template>

<script>
/* eslint-disable */
export default {
  name: 'user',
  props: [ ],
  data () { return {
      mode: "choose",
      user: "",
      pass: ""
    }},
  filters:{
  },
  methods:{	
    toConnect(){
      this.mode = "login";
    },
    toSign(){
      this.mode = "sign";      
    },
    back(){
      this.mode = "choose"
    },
    connect(){
      this.$emit("login",{
        user: this.user,
        pass: this.pass
      });   
    },
  },
  watch:{
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
