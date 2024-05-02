<template>
    <!-- Displaying reaction time score -->
    <p>Reaction time: {{ score }} ms</p>
    <!-- Displaying rank based on score, default "Too Soon" if rank is not set -->
    <h3>{{ rank || "Too Soon" }}</h3>
</template>

<script>
export default {
    name: "Results",
    props: ["score"], // Receiving score as a prop
    data() {
        return {
            rank: null, // Initializing rank as null
        }
    },
    mounted() {
        // Checking if score is not a number, exiting if so
        if (isNaN(this.score)) return

        // Determining rank based on score ranges
        if (this.score < 250) {
            this.rank = "Ninja Fingers" // Assigning rank for very fast reaction
        } else if (this.score < 400) {
            this.rank = "Rapid Reflexes" // Assigning rank for fast reaction
        } else {
            this.rank = "Snail pace..." // Assigning rank for slow reaction
        }
    },
}
</script>
