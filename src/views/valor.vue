<template>

  <div class="inicio">
    <div class="container">
      <div class="col">
           <img src="imge/comida.jpg" href="Home.vue" width="10%" height="10%" class="btn"/>
             <div>

        <b variant="faded" type="light">
          <b href="Home.vue">
            <img src="https://placekitten.com/g/30/30" style="border-radius:40px" >
          </b>
        </b>
        
    </div>
        <h1 class="t1 text-center "> ELIGE LA DIFICULTAD </h1>


        <div class="row m-2 aling-center">
             
            <div class="c1 col-5 col-md-3" >
                 <img src="imge/comida.jpg" width="120%" height="120%" class="btn"  @click="ver(id=1)" />
            </div>

            <div class="c1 col-5 col-md-3" >
                <img src="imge/frutas.jpg" width="120%" height="120%" class="btn"  @click="ver(id=2)"/>
            </div>
            

            <div class="c1 col-5 col-md-3">  
                <img src="imge/jugete.jpg" width="120%" height="120%" class="btn"  @click="ver(id=3)" />
            </div>

            <div class="c1 col-5 col-md-3">
                <img src="imge/pelicula.jfif" width="120%" height="120%" class="btn" @click="ver(id=5)" />
            </div>


            <div class="c1 col-5 col-md-3">
                <img src="imge/anime.jfif" width="120%" height="120%" class="btn" @click="ver(id=5)" />
            </div>

            <div class="c1 col-5 col-md-3">
                <img src="imge/animales.jfif" width="120%" height="120%" class="btn"  @click="ver(id=6)" />
            </div>
           
          
        </div>
      </div>
    </div>

  </div>
</template>


<script>

import HelloWorld from '@/components/HelloWorld.vue'
export default {
name: "Valor",
 props: {
    msg: String
  }
}

</script>