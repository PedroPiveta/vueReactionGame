<template>
    <p @end="endGame">Reaction time {{score}} ms</p>
    <div class="rank">
        {{ rank }}
    </div>
</template>

<script>
export default {
    props: ['score'],
    data(){
        return{
            rank: null
        }
    },
    mounted(){
        if (this.score <250) {
            this.rank = "Wow, that's really fast!"
        } else if(this.score < 400){
            this.rank = "Pretty good!"
        } else {
            this.rank = "You're too slow"
        }
    }
}
</script>

<style scoped>
    p{
        font-size: 1.5rem;
    }
    .rank{
        font-size: 1.4em;
        color: #0faf87;
        font-weight: bold;
    }
</style>