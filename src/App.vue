<template>
    <h1>Reaction Timer</h1>
    <button class="btn" @click="start" :disabled="isPlaying">play</button>
    <Block v-if="isPlaying" :delay="delay" @end="end" />
    <Results v-if="score" :score="score" />
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
    name: "App",
    components: { Block, Results },
    data() {
        return {
            isPlaying: false,
            delay: null,
            score: null,
        }
    },
    methods: {
        start() {
            this.delay = 2000 + Math.random() * 5000
            this.isPlaying = true
            this.score = null
        },
        end(reactionTime) {
            this.score = reactionTime
            this.isPlaying = false
        },
    },
}
</script>

<style>
.btn {
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
    background-color: #0ca37d;
}

.btn:active:not(:disabled) {
    transform: scale(0.95);
}

.btn:disabled {
    background-color: rgb(145, 192, 181);
    cursor: not-allowed;
}
</style>
