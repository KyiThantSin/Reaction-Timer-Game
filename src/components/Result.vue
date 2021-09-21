<template>
	<div>
		<p><b>Reaction Time: {{score}} ms</b></p>
		<br>
		<h2>Your Rank : {{rank}}</h2>
	</div>
</template>

<script>
	export default{
		name:"Result",
		props:["score"],
		data(){
			return{
				rank:null
			}
		},
		mounted(){
			//when this component mounted the DOM this method starts working
			console.log(this.score)
			if(this.score<250){
				this.rank = "Ninja Fingers"
			}else if(this.score<400){
				this.rank = "Rapid Reflexes" 
			}else{
				this.rank = "Snail Pace..."
			}
		}
	};
</script>

<style>
	h2{
		color: green;
	}
</style>