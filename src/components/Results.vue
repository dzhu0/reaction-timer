<template>
    <p>Reaction time: {{ score }} ms</p>
    <h3>{{ rank || "Too Soon" }}</h3>
</template>

<script>
export default {
    props: ["score"],
    data() {
        return {
            rank: null,
        }
    },
    mounted() {
        if (isNaN(this.score)) return

        if (this.score < 250) {
            this.rank = "Ninja Fingers"
        } else if (this.score < 400) {
            this.rank = "Rapid Reflexes"
        } else {
            this.rank = "Snail pace..."
        }
    },
}
</script>
