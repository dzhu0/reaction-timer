<template>
    <!-- Title of the app -->
    <h1>Reaction Timer</h1>
    <!-- Button to start the game, disabled when game is already in progress -->
    <button class="btn" @click="start" :disabled="isPlaying">play</button>
    <!-- Block component to display during the game -->
    <Block v-if="isPlaying" :delay="delay" @end="end" />
    <!-- Results component to display after the game ends -->
    <Results v-if="score" :score="score" />
</template>

<script>
import Block from './components/Block.vue' // Importing Block component
import Results from './components/Results.vue' // Importing Results component

export default {
    name: "App",
    components: { Block, Results }, // Registering components
    data() {
        return {
            isPlaying: false, // Flag to indicate if game is in progress
            delay: null, // Delay for when player can click
            score: null, // Reaction time score
        }
    },
    methods: {
        // Method to start the game
        start() {
            // Setting a random delay between 2000 and 7000 milliseconds
            this.delay = 2000 + Math.random() * 5000
            this.isPlaying = true // Setting isPlaying to true to indicate game is in progress
            this.score = null // Resetting score
        },
        // Method to handle end of game
        end(reactionTime) {
            this.score = reactionTime // Setting the reaction time score
            this.isPlaying = false // Setting isPlaying to false to indicate game has ended
        },
    },
}
</script>

<style>
/* Styles for button */
.btn {
    /* Button styling */
    display: block;
    background-color: #0faf87;
    color: white;
    font-family: Inter, sans-serif;
    font-weight: bold;
    text-transform: uppercase;
    border: none;
    border-radius: 12px;
    padding: 12px 36px;
    margin-inline: auto;
    cursor: pointer;
}

.btn:hover {
    /* Button hover styling */
    background-color: #0ca37d;
}

.btn:active:not(:disabled) {
    /* Button active styling */
    transform: scale(0.95);
}

.btn:disabled {
    /* Button disabled styling */
    background-color: rgb(145, 192, 181);
    cursor: not-allowed;
}
</style>
