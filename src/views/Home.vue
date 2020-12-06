<template>

  <div class="inicio">
    <div class="container">
      <div class="col" id="ini" style="display: none;">
        <h1 class="t1 text-center "> ENCUENTRALO </h1>

        <div class="row  aling-center">
          <div class="col-5 col-md-4" v-for="(categ, index) in categorias" :key="index">
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
    };
   },
  components: {
    HelloWorld
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
          
          this.$router.push('/valor')

        }
    },


  }
 
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

</style>