<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        click me
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
        console.log("component mounted");
           setTimeout(() => {
            this.startTimer();
            this.showBlock = true;
           },this.delay)
       },
       methods: {
        startTimer() {
            this.timer = setInterval(()=>{
                this.reactionTime += 10
            },10);
        },
        stopTimer() {
            clearInterval(this.timer);            
            this.$emit('end', this.reactionTime);
        }
       },
       updated() {
        console.log("component updated");
       },
    }
</script>

<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background-color: rgb(59, 145, 116);
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>