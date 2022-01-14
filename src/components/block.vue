<template>
    <p>Get ready...</p>
  <div class="block" v-if="showBlock" @click="stopTimer">
      Click me
  </div>
</template>

<script>

export default {
    props: ['delay'],
    data(){
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted(){
        console.log('Component mounted!') //This will be showed when the component is mounted.

        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)  
    },

    methods:{
        startTimer(){
            this.timer = setInterval(()=>{
                this.reactionTime +=10
            },10)
        },
        stopTimer(){
            clearInterval(this.timer)
            this.$emit('end', this.reactionTime)
        }
    },

    updated(){
        console.log('Component updated!')
    },

    unmounted(){
        //Only shows if the component is unmounted
    }
}
</script>

<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background: #0faf87;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>