<template>
    
<div id="app" style="display:none;">
    <div class="d-flex flex-row justify-content-center py-3">
    <div class="turns p-3"><span class="btn btn-danger">Turns : <span class="badge" :class="finish ? 'badge-success' : 'badge-light'">{{turns}}</span> </span></div>
    <div class="totalTime p-3"><span class="btn btn-warning">Total Time : <span class="badge" :class="finish ? 'badge-success' : 'badge-light'">{{min}} : {{sec}}</span></span></div>
    <div class="totalTime p-3"><button class="btn btn-info" @click="reset" :disabled="!start">Restart</button></div>
</div>
    <div class="row">
        <div class="col-md-6 col-lg-6 col-xl-5 mx-auto">
             <div class="row justify-content-md-center">
               <!--   <div v-for="(card, index) in cards" class="col-auto mb-3 flip-container" :class="{ 'flipped': card.isFlipped }" @click="flipCard(card)" :key="index"> -->
                  <div v-for="(card, index) in memoryCards" class="col-auto mb-3 flip-container" :class="{ 'flipped': card.isFlipped, 'matched' : card.isMatched }" @click="flipCard(card)" :key="index">
  
                    <div class="memorycard">
                        <div class="front border rounded shadow"><img width="100" height="150" src="imge/fon.jfif"></div>
                        <div class="back rounded border"><img width="100" height="150" :src="'imge/'+card.img"></div>
                               
                    </div>
                 </div>
            </div>
        </div>
    </div>
</div>

</template>

<script>
export default {
    
    
    name: 'iniciar',
    data() {
            return{
                    cards: [
                {
                    name: 'frutas',
                    img: 'frutas.jpg',
                },
                {
                    name: 'comida',
                    img: 'comida.jpg',
 
                },
                {
                    name: 'jugete',
                    img: 'jugete.jpg',

                },
                {
                    name: 'pelicula',
                    img: 'pelicula.jfif',

                },
                {
                    name: 'anime',
                    img: 'anime.jfif',

                },
                {
                    name: 'animales',
                    img: 'animales.jfif',

                },
            ],

            memoryCards: [],
            flippedCards: [],
            finish: false,
            start: false,
            turns: 0,
            totalTime: {
                minutes: 0,
                seconds: 0,
            },
            } 
    },
   
     created(){
        this.reset();

        this.cards.forEach((card) => {
            Vue.set(card,'isFlipped',false);
            Vue.set(card,'isMatched',false);
        });

        this.memoryCards = _.shuffle(this.memoryCards.concat(_.cloneDeep(this.cards), _.cloneDeep(this.cards)));
    },


    
    methods:{

        flipCard(card){

     if(card.isMatched || card.isFlipped || this.flippedCards.length === 2)
            return;

    
    if(!this.start){
        this._startGame();
    }

    card.isFlipped = true;

    if(this.flippedCards.length < 2)
        this.flippedCards.push(card);
    if(this.flippedCards.length === 2)    
        this._match(card);
},
/* ///////////////////////////// */
        _match(card){
            this.turns++;
    if(this.flippedCards[0].name === this.flippedCards[1].name){
        setTimeout(() => {
    this.flippedCards.forEach(card => card.isMatched = true);
    this.flippedCards = [];

    //All cards matched ?
   if(this.memoryCards.every(card => card.isMatched === true)){
    clearInterval(this.interval);
    this.finish = true;
}

}, 400);
    }
    else{
        setTimeout(() => {
            this.flippedCards.forEach((card) => {card.isFlipped = false});
            this.flippedCards = [];
        }, 800);
    }
},

        _startGame(){
    this._tick();
    this.interval = setInterval(this._tick,1000);
    this.start = true;
},


_tick(){
    if(this.totalTime.seconds !== 59){
         this.totalTime.seconds++;
         return
     }

     this.totalTime.minutes++;
     this.totalTime.seconds = 0;
},

        reset(){
    clearInterval(this.interval);

    this.cards.forEach((card) => {
        Vue.set(card, 'isFlipped',false);
        Vue.set(card, 'isMatched',false);
    });

    setTimeout(() => {  
        this.memoryCards = [];
        this.memoryCards = _.shuffle(this.memoryCards.concat(_.cloneDeep(this.cards), _.cloneDeep(this.cards)));
        this.totalTime.minutes = 0;
        this.totalTime.seconds = 0;
        this.start = false;
        this.finish = false;
        this.turns = 0;
        this.flippedCards = [];
           
        }, 600);
    
},


    },

    computed:{
    sec(){
        if(this.totalTime.seconds < 10){
            return '0'+this.totalTime.seconds;
        }
        return this.totalTime.seconds;
    },
    min(){
        if(this.totalTime.minutes < 10){
            return '0'+this.totalTime.minutes;
        }
        return this.totalTime.minutes;
    }
}


}


</script>

<style>

.flip-container {
        -webkit-perspective: 1000;
        -moz-perspective: 1000;
        -o-perspective: 1000;
        perspective: 1000;
        min-height: 120px;
        cursor: pointer;
    }
    .front,
    .back {
        -webkit-backface-visibility: hidden;
        -moz-backface-visibility: hidden;
        -o-backface-visibility: hidden;
        backface-visibility: hidden;
        -webkit-transition: 0.6s;
        -webkit-transform-style: preserve-3d;
        -moz-transition: 0.6s;
        -moz-transform-style: preserve-3d;
        -o-transition: 0.6s;
        -o-transform-style: preserve-3d;
        -ms-transition: 0.6s;
        -ms-transform-style: preserve-3d;
        transition: 0.6s;
        transform-style: preserve-3d;
        top: 0;
        left: 0;
        width: 100%;
    }
    .back {
        -webkit-transform: rotateY(-180deg);
        -moz-transform: rotateY(-180deg);
        -o-transform: rotateY(-180deg);
        -ms-transform: rotateY(-180deg);
        transform: rotateY(-180deg);
        position: absolute;
    }
    .flip-container.flipped .back {
        -webkit-transform: rotateY(0deg);
        -moz-transform: rotateY(0deg);
        -o-transform: rotateY(0deg);
        -ms-transform: rotateY(0deg);
        transform: rotateY(0deg);
    }
    .flip-container.flipped .front {
        -webkit-transform: rotateY(180deg);
        -moz-transform: rotateY(180deg);
        -o-transform: rotateY(180deg);
        -ms-transform: rotateY(180deg);
        transform: rotateY(180deg);
    }
    .matched{
   opacity: 0.3;
}
</style>