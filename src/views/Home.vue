<template>

  <div class="inicio">
    <div class="container">
      <div class="col">
        <h1 class="t1 text-center "> ENCUENTRALO </h1>

        <div class="row  aling-center">
          <div v-for="(categ, index) in categorias" :key="index">
              <div class="t1 row text-center">
                 <img :src="categorias[index]" width="120%" height="120%" class="btn col-5 col-md-3"  @click="ver(id=index)" />  
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
            val:0,
            id:0,
            cate:0,
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