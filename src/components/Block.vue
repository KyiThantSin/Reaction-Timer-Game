<template>
	<div id="block" v-if="showBlock" @click="stopTimer">
		<h2>Click Me !! </h2>
	</div>
</template>

<script>
	export default{
		name:'Block',
		props:['delay'],
		data(){
			return{
				showBlock:false,
				reactionTime:0,
				timer:null
			}
		},
		mounted(){
			console.log("componet mounted")
			setTimeout(()=>{
				this.showBlock = true
				console.log(this.delay),
				this.startTimer()
			},this.delay)
		},
		methods:{
			startTimer(){
				this.timer = setInterval(()=>{
					this.reactionTime +=10
				},10)
			},
			stopTimer(){
				clearInterval(this.timer)
				this.$emit("end", this.reactionTime)
			}
		}
	};
</script>

<style>
	#block{
		margin-top: 20px;
		height: 100px;
		border: 1px solid lightgrey;
		padding: 20px;
		text-align: center;
		font-size:20px;
		background-color: lightpink;
	}
</style>