<template>
    <!-- Dynamically apply 'start' class based on 'start' data property -->
    <div class="block" :class="{start: start}" @click="stopTimer">
        <!-- Displaying message (initially "wait" then "click me") -->
        {{ message }}
    </div>
</template>

<script>
export default {
    name: "Block",
    props: ["delay"], // Receiving delay as a prop
    data() {
        return {
            message: "wait", // Initial message
            start: false, // Flag to indicate if timer has started
            startTime: null, // Start time of the timer
            reactionTime: null, // Time taken to react
        }
    },
    mounted() {
        // Setting timeout to change message and start the timer after 'delay' milliseconds
        setTimeout(() => {
            this.message = "click me" // Changing message
            this.start = true // Starting the timer
            this.startTimer() // Starting the timer
        }, this.delay)
    },
    methods: {
        // Method to start the timer
        startTimer() {
            this.startTime = Date.now() // Setting start time of the timer
        },
        // Method to stop the timer on click
        stopTimer() {
            // If timer hasn't started, emit 'end' event with "N/A"
            if (!this.start) return this.$emit('end', "N/A")

            // Calculating reaction time and emitting 'end' event with the reaction time
            this.reactionTime = Date.now() - this.startTime
            this.$emit('end', this.reactionTime)
        },
    },
}
</script>

<style>
.block {
    /* Styling for the block element */
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
    /* Styling for the block element when 'start' is true */
    background-color: #0faf87;
}
</style>
