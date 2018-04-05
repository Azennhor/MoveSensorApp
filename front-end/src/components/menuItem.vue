<template>
  <div @click="switchTo" :class="active | toClass">
    <img src="icon" alt="">{{name}}
  </div>
</template>

<script>
/* eslint-disable */
export default {
  name: 'menuItem',
  props: [ "name", "page", "icon"],
  data () { return {
			active: false,
    }},
  filters:{
		toClass(does){
			let style = "case";

			if (does)
				style += " active";
			return style;
		}
  },
	methods:{
		switchTo(){
			this.$emit("changepage", this.name);
		}
	},
	watch:{
		page(){
			if( this.page === this.name)
				this.active = true;
			else
				this.active = false;
		}
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	.case
	{
		width: 100%;

		background: lightblue;

    cursor: pointer;
	}
	.active
	{
		background: crimson;
	}
</style>
