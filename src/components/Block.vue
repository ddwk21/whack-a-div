<template>
  <div class="block" v-if="showBlock" @click="playEvent" :style="{marginRight: position + 'px'}">
    Click Me!
  </div>
</template>

<script>
export default {
    props:['delay'],
    data() {
      return {
        showBlock: false,
        timer: null,
        reactionTime: 0,
        position: null,
        blockCounter: 0,
        maxBlocks: 5,
        totalReactionTime: 0,
      }
    },

    mounted() {
      console.log('Component Mounted')
      setTimeout(() => {
        this.showBlock = true;
        this.startTimer()
      }, this.delay)





    },
    updated() {
      console.log('Component Updated')
    },
    methods:{
      startTimer(){
        this.timer = setInterval(() => {
          this.reactionTime += 10
        }, 10)
      },

      playEvent(){
        
        if(this.blockCounter === (this.maxBlocks-1))
        {  
          clearInterval(this.timer)
          console.log(this.reactionTime)
          this.reactionTime = this.totalReactionTime/5
          this.$emit('score', this.reactionTime)
        }else{
          this.totalReactionTime += this.reactionTime;
          this.blockCounter++

          this.showBlock = false;
          this.determinePosition;
          this.reactionTime = 0;
          setTimeout(() => {
            this.showBlock = true;
            this.startTimer()
          }, this.delay)
          
        }
      },

      determinePosition(){
        this.position = (Math.floor(Math.random*500)) * (Math.round(Math.random()) * 2 - 1)
        console.log(this.position)
      }
    }
    
}
</script>

<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background: rgb(63, 120, 120);
        color: white;
        text-align: center;
        padding: 100px 0;
        margin-top: 40px;
    }

</style>