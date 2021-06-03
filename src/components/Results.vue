<template>
  <p>Reaction Time - {{ score }}ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
    name: 'Results',
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        this.rank = this.score < 250 ? '✈ Ninja' : this.score < 400 ? '🚆 Rapid' : '🐢...Slow'
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