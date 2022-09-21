<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import HelloTest from './components/HelloTest.vue'
import Block from './components/Block.vue';
</script>
<script>
//this is how we can trigger custom events
export default {

  // components:{Block},
  data(){
    return{
      openModal:false,
      name:"Humna",
      isPlaying:false,
      delay:null
    }
  },
  methods:{
    toggleModal(){
            console.log(" modal event triggered")

      this.openModal=!this.openModal
    },
    changeName(){
      this.name="sana"

    },
    greet(event){
      alert(`Hello ${this.name}!`)
    },
    play(){
      this.delay=2000 + Math.random() * 5000
      this.isPlaying=true
      console.log(this.delay,' delayyyyyyy')

    }
  }
}
</script>

<template>
  <div class="header">
    <HelloTest btnName="close" @close="toggleModal" />
  <button @click="changeName">
  change NAme
  </button>
  <button @click="greet">Greet</button>

  </div>

<div class="game">
  <h5>Reaction Timer Game</h5>
  <button class="btn btn-dark" @click="play" :disabled="isPlaying" >Play</button>
  <Block v-if="isPlaying" :delay="delay"  />


</div>



</template>



<style scoped>
header {
  line-height: 1.5;
  margin-top: 5px;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}
.game{
  margin-top: 150px;
  margin-left: -12px;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
<!-- mounting" (adding nodes to the DOM), "unmounting" (removing them from the DOM) -->