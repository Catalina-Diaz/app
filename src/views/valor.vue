<template>

  <div class="inicio">
    <div class="container">
      <div class="col">
        <h1 class="t1 text-center "> DIFICULTAD </h1>
        <img src="imge/home.png" @click="inicio()" class="btn" width="15%" height="50%" style="border-radius:100px"/>
        <div class="row  aling-center">
          <div class="col-5 col-md-4" v-for="(categ, index) in categorias" :key="index">
              <div class="c1 ">
                 <img :src="categorias[index]" width="120%" height="120%" class="btn2 btn"  @click="ver(id=index)" />  
              </div> 
          </div>
        </div>


      </div>
    </div>
  </div>
</template>


<script>

export default {
  name: 'valor',
   data(){
        return{
            categorias: ["imge/comida.jpg","imge/frutas.jpg","imge/jugete.jpg",
            "imge/pelicula.jfif","imge/anime.jfif","imge/animales.jfif"],
            ingreso:1,
            val:0,
            valo:0,
            id:0,
            cate:0,
    };
   },
 

  mounted() {
        this.ver(),
        this.inicio()
    },
  methods:{
    inicio(){

          this.val = this.val + this.ingreso
          
          if(this.val==2){
          this.val=0,
          this.$router.push('/')
            }

    },

    ver(id){
        this.id
        this.valo = this.valo + this.ingreso
        if(this.valo==2){
          this.valo=1,
          /* console.log(this.val) */
          console.log(id)
        /*   this.$router.push('/valor') */
        }
       
    },

  }
 
}
</script>
<style>
.t2{
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}
.btn2{
  border-radius: 20% ;
  border-collapse: inherit;
  border-block-width: 5px;
  border-block-color: rgb(216, 17, 173);
}
</style>