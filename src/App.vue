<template>
  <h1>Ninja Reaction Timer ^^</h1>
  <div class="intro">
    <h3>How Quick Is Your Reaction ? <br></h3>
    To Test it <b> Click under the pinky Block!!</b>
  </div>
  <br>
  <button @click="start" :disabled="isPlaying">Play</button>
  <br>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>  <!--Custome Event(end)-->
  <br>
  <Result v-if="showResult" :score="score"/>
</template>


<script>
import Block from "./components/Block.vue"
import Result from "./components/Result.vue"

export default {
  name: 'App',
  components: {
    Block,Result
  },
  data(){
    return{
      delay:null,
      isPlaying:false,
      score:null,
      showResult:false
    }
  },
  methods:{
    start(){
      this.isPlaying = true
      this.delay= 2000 + Math.random() * 5000
      this.showResult = false
      console.log(this.delay)
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResult = true
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button{
  padding: 10px;
  border: 1px solid lightpink;
  background-color: hotpink;
  cursor: pointer;
  width: 80px;
  font-family: monospace;
  color: white;
  font-size: 20px;
  border-radius: 10px;

}
button:active{
  border: 2px solid hotpink;
  background-color: lightpink;
}
.intro{
  color: green;
}
</style>
