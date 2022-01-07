<template>
    <div v-if="showBlock" @click="stopTimer" class="block rounded w-25 p-5 bg-info text-white text-center my-5 mx-auto">
        Click Me
    <!-- <p>Reaction Time - {{ reactionTime }} ms</p> -->
    </div>
</template>


<script>
export default {
    props: ['delay'],
    
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
            //console.log(this.delay)
        }, this.delay)
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() =>{
                this.reactionTime += 10
            },10)
        },
        stopTimer() {
            clearInterval(this.timer)
            // this.showBlock = false
            this.$emit('end', this.reactionTime)
        }
    },
}
</script>

<style>

</style>