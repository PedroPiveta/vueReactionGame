<template>
    <p @end="endGame">Reaction time {{score}} ms</p>
    <div v-if="score < 400">
        <p>pretty fast :)</p>
    </div>
    <div v-else>
        <p>you're too slow :(</p>
    </div>
</template>

<script>
    export default {
        props: ['score']
    }
</script>

<style scoped>
    p{
        font-size: 1.5rem;
    }
</style>