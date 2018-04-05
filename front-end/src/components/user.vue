<template>
  <div class="full">
    <div v-if="mode === 'choose'" class="layout">
      <!-- <img src="./assets/logIcon.png" alt=""> -->
      <div class="lowButtons">
        <button class="button" @click="toConnect">se connecter</button>
        <button class="button" @click="toSign">s'enregistrer</button>
      </div>
    </div>
    <div v-if="mode === 'login'" class="layout">
      <div class="fields">
        <input type="text" name="login" placeholder="nom d'utilisateur" v-model="user">
        <input type="password" name="passw" placeholder="mot de passe" v-model="pass">
      </div>
      <div class="buttons">
        <button class="button" @click="connect">se connecter</button>
        <button class="button" @click="back">retour</button>
      </div>
    </div>
    <div v-if="mode === 'sign'" class="layout">
      <div class="fields">
        <input type="text" name="login" placeholder="nom d'utilisateur" v-model="user">
        <input type="password" name="passw" placeholder="mot de passe" v-model="pass">
      </div>
      <div class="buttons">
        <button class="button" @click="sign">s'enregistrer</button>
        <button class="button" @click="back">retour</button>
      </div>
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
      let send = {
        mode: this.mode,
        user: this.user,
        pass: this.pass
      };

      this.$emit("login", send);
    },
    sign(){

    }
  },
  watch:{
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.layout
{
  display: grid;

  grid-template-columns: 20% auto 20%;
  grid-template-rows: 1fr auto auto auto auto 1fr;
  grid-template-areas:
    ". . ."
    ". logo ."
    ". fields ."
    ". buttons ."
    ". lowButtons ."
    ". . .";

  width: 100%;
  height: 100%;
}
.logo{
  grid-area: logo;
}
.fields
{
  grid-area: fields;
}
.buttons
{
  grid-area: buttons;
}
.lowButtons
{
  grid-area: lowButtons;
}
</style>
