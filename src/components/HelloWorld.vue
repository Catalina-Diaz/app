<template>
  <div class="hello">
    <!-- <h1>{{ msg }}</h1> -->
    

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  date: {
      a : "cuadro.png",
  },
  props: {
    msg: String
  }
}
</script>

<style>

.t1{
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  border-block: 10%;
  border-color:rgb(43, 214, 226);
}
img{
  border-radius: 20% ;
  border-collapse: inherit;
}
</style>
