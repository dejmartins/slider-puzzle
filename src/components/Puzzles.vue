<template>
    <h1>Select a puzzle</h1>
    <div  v-for="p of puzzles" :key="p.id" class="row">
        <div>
            <img :src="require(`../assets/cars/${p.image}`)" />
        </div>
        <div>
            <h2>{{ p.title }}</h2>
        </div>
        <div class="play-button">
            <button @click="selectPuzzle(p)">Play</button>
        </div>
    </div>
</template>
<script>
    export default{
        data(){
            return{
                puzzles: [
                    {
                        id: "hyundaicharge",
                        image: "hyundaicharge.jpg",
                        title: "Hyundai Charge"
                    }, 
                    {
                        id: "hyundaiforest",
                        image: "hyundaiforest.jpg",
                        title: "Hyundai Forest"
                    }, 
                    {
                        id: "redcharlie",
                        image: "redcharlie.jpg",
                        title: "Red Charlie"
                    }, 
                ]
            }
        },
        methods: {
            selectPuzzle(puzzle){
                this.$emit("puzzle-changed", puzzle.id)
            }
        }
    }
</script>
<style scoped>
    .row {
        display: flex;
        max-width: 90vw;
        flex-wrap: wrap;
        justify-content: space-between;
    }

    .row img {
        width: 100px;
    }

    .row .play-button {
        padding-top: 25px;
    }
</style>