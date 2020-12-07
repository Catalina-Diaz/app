<template>

  <div class="inicio">
    <div class="container">
      <div class="col" id="ini" style="display: none;">
        <h1 class="t1 text-center "> ENCUENTRALO </h1>

        <div class="row  aling-center">
          <div class="col-sm-6 col-md-4 col-lg-3 col-xl-3  mx-auto" v-for="(categ, index) in categorias" :key="index">
              <div class="c1 ">
                 <img :src="categorias[index]" width="120%" height="120%" class="btn1 btn"  @click="ver(id=index)" />  
              </div> 
          </div>
        </div>
      </div>

      <div class="col" id="difi" style="display: block; ">
        <h1 class="t1 text-center " > DIFICULTAD </h1>
        <img src="imge/home.png" @click="inicio()" class="btn" width="15%" height="50%" style="border-radius:100px"/>
        <div class="row  aling-center">
          <div class="col-5 col-md-4" v-for="(dific, inde) in dificultad" :key="inde">
              <div class="c1 ">    
                    <label class="btn2 btn" @click="mostrar(ide=inde)" > 3 X {{inde+2}} </label>
                 <!-- <img :src="dific[index]" width="100%" height="100%" class="btn2 btn"  @click="ver(id=inde)" />   -->
              </div> 
          </div>
        </div>
       </div> 


       <div class="col" id="jue" style="display: none; ">
        <h1 class="t1 text-center " > inciando el juego </h1>
        <img src="imge/home.png" @click="inicio()" class="btn" width="15%" height="50%" style="border-radius:100px"/>

        <div class="row  aling-center">
          <div class="col-5 col-md-4" v-for="(categ, ultimo) in categorias" :key="ultimo">
              <div class="c1 ">    
                     <img :src="categorias[ultimo]" width="120%" height="120%" class="btn1 btn"  @click="ver(ic=ultimo)" />   
              </div> 
          </div>
        </div>
       </div>    


    </div>

    <div id="app" style="display:block;">
    <div class="d-flex flex-row justify-content-center py-3">
        <div class="turns p-3"><span class="btn btn-danger">Turns : <span class="badge" :class="finish ? 'badge-success' : 'badge-light'">{{turns}}</span> </span></div>
        <div class="totalTime p-3"><span class="btn btn-warning">Total Time : <span class="badge" :class="finish ? 'badge-success' : 'badge-light'">{{min}} : {{sec}}</span></span></div>
        <div class="totalTime p-3"><button class="btn btn-info" @click="reset" :disabled="!start">Restart</button></div>
    </div>
    <div class="row">
        <div class="col-md-8 col-lg-10 col-xl-12  mx-auto">
             <div class="row justify-content-md-center">
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
  </div>



</template>

<script>

import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
   data(){
        return{
            categorias: ["imge/comida.jpg","imge/frutas.jpg","imge/jugete.jpg",
            "imge/pelicula.jfif","imge/anime.jfif","imge/animales.jfif"],
            ingreso:1,
            val:1,
            id:0,
            cate:0,

            dificultad: ["1","2","3","4","5","6"],
            valo:1,
            ide:0,
            inde:3,
            ingre:1,
            ic:0,

            image1:[],
            image2:[],
            image3:[],
            image4:[],
            image5:[],
            image6:[],
            /* ///////////// */
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
    };
   },
   created(){
        this.reset();

        this.cards.forEach((card) => {
            Vue.set(card,'isFlipped',false);
            Vue.set(card,'isMatched',false);
        });

        this.memoryCards = _.shuffle(this.memoryCards.concat(_.cloneDeep(this.cards), _.cloneDeep(this.cards)));
    },

  
  mounted() {
        this.ver()
        this.mostrar(),
        this.inicio()
    },
  methods:{
    inicio(){

          this.val = this.val + this.ingreso
          if(this.val==2){
          this.val=1,
          this.id=8;
          this.ide=8;
          /* this.$router.push('/') */
          document.getElementById("difi").style.display="none";
          document.getElementById("ini").style.display="block";
          document.getElementById("jue").style.display="none";
          
            }

    },
    ver(id){
        this.id
        this.val = this.val + this.ingreso
        if(this.val==2){
         
          this.val=1,
          /* console.log(this.val) */
          console.log(id)
          document.getElementById("difi").style.display="block";
          document.getElementById("ini").style.display="none";
          document.getElementById("jue").style.display="none";
         /*  this.$router.push('/valor') */
        }
    },
    mostrar(ide){
        this.ide
        this.valo = this.valo + this.ingre
        /* document.log(ingre, "este es el nuemro") */
        if(this.valo==2){
          this.valo=1,
          /* console.log(this.val) */
          console.log(ide)
          document.getElementById("difi").style.display="none";
          document.getElementById("ini").style.display="none";
          document.getElementById("jue").style.display="block";
          /* 
          this.$router.push('/valor') */

        }
    },

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



      _match(card){
            this.turns++;
             if(this.flippedCards[0].name === this.flippedCards[1].name){
          setTimeout(() => {
            this.flippedCards.forEach(card => card.isMatched = true);
            this.flippedCards = [];
               if(this.memoryCards.every(card => card.isMatched === true)){
                 clearInterval(this.interval);
                 this.finish = true;}
                 }, 400);
             }else{
          setTimeout(() => {
              this.flippedCards.forEach((card) => {card.isFlipped = false});
              this.flippedCards = [];
              }, 800); 
             }
          },

          /* ///////////////INICIO DE JUEGO CRONOMETRO//////// */
       _startGame(){
            this._tick();
            this.interval = setInterval(this._tick,1000);
            this.start = true;
        },

        /* ////////////TIEMPO TRANSCURRIDO ////////// */
        
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
},

 
}
</script>

<style>
.t1{
  padding-top:8% ;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  border-block: 10%;
  border-color:rgb(43, 214, 226);
}

.btn1{
  border-radius: 20% ;
  border-collapse: inherit;
  border-block-width: 5px;
  border-block-color: rgb(17, 186, 216);
}
.c1{
  margin-top: 8%;
  margin-right: 8%;
}
.btn2{
  border-radius: 20% ;
  background: rgb(219, 203, 203);
  width: 100% ;
  height: 100%;
  border-collapse: inherit;
  border-block-width: 5px;
  border-block-color: rgb(216, 17, 173);
  font-size: 50px;
  font-family:  algerian;

}
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