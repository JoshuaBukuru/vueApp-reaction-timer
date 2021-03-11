<template>
   <p > Reaction Time: {{ score }} ms</p>
   <p class="rank"> {{ rank }} </p>

</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if (this.score < 250){
            this.rank = 'You have extremely fast reflexes'
        } else if (this.score < 400) {
            this.rank = 'Rapid reflexes'
        } else {
            this.rank = 'You have a snail pace reflex'
        }
    }

}
</script>

<style>
  .rank {
      font-size: 1.4em;
      color: #0faf87;
      font-weight: bold;
  }


</style>