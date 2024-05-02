<template>
    <div class="block" :class="{start: start}" @click="stopTimer">
        {{ message }}
    </div>
</template>

<script>
export default {
    props: ["delay"],
    data() {
        return {
            message: "wait",
            start: false,
            startTime: null,
            reactionTime: null,
        }
    },
    mounted() {
        setTimeout(() => {
            this.message = "click me"
            this.start = true
            this.startTimer()
        }, this.delay)
    },
    methods: {
        startTimer() {
            this.startTime = Date.now()
        },
        stopTimer() {
            if (!this.start) return this.$emit('end', "N/A")

            this.reactionTime = Date.now() - this.startTime
            this.$emit('end', this.reactionTime)
        },
    },
}
</script>

<style>
.block {
    width: 80vw;
    max-width: 400px;
    height: 80vw;
    max-height: 400px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: rgb(240, 25, 25);
    color: white;
    font-weight: bold;
    text-transform: uppercase;
    border-radius: 24px;
    margin: 36px auto;
    cursor: pointer;
}

.block.start {
    background-color: #0faf87;
}
</style>
