<template>

  <div class="inicio">
    <div class="container">
      <div class="col">
        <h1 class="t1 text-center "> ENCUENTRALO </h1>


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
     <!--   {{msg="zxczxc"}} -->

     <!-- <HelloWorld/> -->
 
<!-- 
      <t v-for="categ in categorias" :key="categ.id" >
            <li class="nav-item active">
                  <img src="cuadro.png" width="90%" height="90%"/>
           </li>   
      </t>
       -->
      
  </div>
</template>

<script>

import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
   data(){
        return{
            categorias: ["1"],
            ingreso:1,
            val:0,
            id:0,
    };
   },
  components: {
    HelloWorld
  },

  mounted() {
        this.ver()
    },
  methods:{
    
    ver(id){
        this.id
        this.val = this.val + this.ingreso
        if(this.val==2){
         
          this.val=1,
          /* console.log(this.val) */
          console.log(id)
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

.btn{
  border-radius: 20% ;
  border-collapse: inherit;
  border-block-width: 5px;
  border-block-color: rgb(17, 186, 216);
  
}
.c1{
  margin-top: 8%;
  margin-right: 8%;
}
</style>