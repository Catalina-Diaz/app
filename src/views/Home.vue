<template>

  <div class="hme">
    <div class="container m-3">
      <div class="col">
        <h1 class="t1 text-center "> ENCUENTRALO </h1>


        <div class="row m-2">

            <div class="col-6 btn">
                <img src="comida.jpg" width="90%" height="90%"/>
            </div>

            <div class="col-6 btn">
                <img src="frutas.jpg" width="90%" height="90%"/>
            </div>

            <div class="col-6">
                <img src="jugete.jpg" width="90%" height="90%"/>
            </div>
            <div class="col-6">
                <img src="pelicula.jfif" width="90%" height="90%"/>
            </div>
            <div class="col-6">
                <img src="anime.jfif" width="90%" height="90%"/>
            </div>
            <div class="col-6">
                <img src="animales.jfif" width="90%" height="90%"/>
            </div>
           
        </div>
      </div>
    </div>
     
    <HelloWorld/>
      <t v-for="categ in categorias" :key="categ.id" >
            <li class="nav-item active">
                  <img src="cuadro.png" width="90%" height="90%"/>
           </li>   
      </t>
      
      
  </div>
</template>

<script>

import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
   data(){
        return{
            categorias: ["1"],
            a : "cuadro.png",
    };
   },
  components: {
    HelloWorld
  }
}
</script>
