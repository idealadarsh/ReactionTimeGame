<template>
  <div @click="stopTimer" v-if="showBlock" class="block">
      <h3>Click Me</h3>
  </div>
</template>

<script>
export default {
    name: 'Block',
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted() {
        setTimeout(() => this.showBlock = true, this.delay)
        this.startTimer()
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => this.reactionTime += 1, 10)
        },
        stopTimer() {
            clearInterval(this.timer)
            this.$emit('end', this.reactionTime)
        }
    }
}
</script>

<style>
.block {
    width: 400px;
    border-radius: 20px;
    background: #0faf97;
    color: #fff;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>