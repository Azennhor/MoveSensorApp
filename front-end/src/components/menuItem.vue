<template>
  <div @click="switchTo">
    <img :src="pic" :class="active | toClass" >
  </div>
</template>

<script>
/* eslint-disable */
export default {
  name: 'menuItem',
  props: [ "pic", "name", "page" ],
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
		width: 2rem;
		height: 2rem;

		background: lightblue;
	}
	.active
	{
		background: crimson;
	}
</style>
