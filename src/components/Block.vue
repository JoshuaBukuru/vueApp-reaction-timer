
<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    <p>click</p>
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0,
        }
    },
    //Life cycle hooks
    mounted() { //when component is mounted to DOM then its fired
        console.log('component is mounted')
        setTimeout(() => { // We wait for a while before the green block appears
            this.showBlock = true
            this.startTimer()
            console.log(this.delay)
        }, this.delay)
    },
    updated() { //Fire when data inside component is updated
        console.log('data has been updated')
    },
    unmounted() { 
        console.log("unmounted") //only fires when block tag in app is unmounted
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() =>{
                this.reactionTime += 10
            }, 10)
        },
    stopTimer() {
        clearInterval(this.timer)
        //Custom event to emit data to app.vue, we can send data along with it
        this.$emit('end', this.reactionTime)

    }

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