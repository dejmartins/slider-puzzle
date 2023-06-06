<script>
    import moment from "moment";

    const correctPuzzleArray = [
        "image_part_001.jpg",
        "image_part_002.jpg",
        "image_part_003.jpg",
        "image_part_004.jpg",
        "image_part_005.jpg",
        "image_part_006.jpg",
        "image_part_007.jpg",
        "image_part_008.jpg",
        "image_part_009.jpg",
    ];

    export default{
        name: "SliderPuzzle",
        props: {
            puzzleId: {
                type: String,
                default: "red-charlie"
            }
        },
        data(){
            return {
                correctPuzzleArray,
                shuffledPuzzleArray: [...correctPuzzleArray].sort(
                    () => Math.random() - 0.5
                ),
                indexesToSwap: [],
                timer: undefined,
                startDateTime: new Date(),
                currentDateTime: new Date()
            }
        },
        computed: {
            isWinning(){
                for(let i = 0; i < correctPuzzleArray.length; i++){
                    if(correctPuzzleArray[i] !== this.shuffledPuzzleArray[i]){
                        return false
                    }
                }
                return true
            },
            elapsedDiff(){
                const currentDateTime = moment(this.currentDateTime);
                const startDateTime = moment(this.startDateTime)
                return currentDateTime.diff(startDateTime)
            },
            elapsedTime(){
                return moment.utc(this.elapsedDiff).format("HH:mm:ss")
            }
        }
    }
</script>