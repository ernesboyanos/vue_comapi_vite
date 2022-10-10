<script setup>
  
  import {ref, computed} from 'vue';

  const arrayFavoritos = ref([]);

  const agregar = () => {
      arrayFavoritos.value.push(counter.value);
  }

  const bloquearBoton = computed(()=>{
      const numSearch  = arrayFavoritos.value.find((num)=>num === counter.value);
      if(numSearch===0) return true;
      return numSearch ? true : false;


  });

  var name = 'Ernesto';
  const counter = ref(0);
  const increment = () => {    
    counter.value=counter.value+1;
  }
  const decrement = () => {    
    counter.value=counter.value-1;
  }
  const reset = () => {    
    counter.value=0;
  }

 const counterClass = computed(() => {
        if (counter.value > 0) {
            return 'positivos'
        }
        if (counter.value < 0) {
            return 'negativos'
        }
        if (counter.value === 0) {
            return 'zero'
        }

 })


</script>

<template>
  <div class="container">
  <h1> Hola {{name.toUpperCase()}}</h1>
  <h2 :class="counterClass">{{counter}}</h2>
  <div class="btn btn-group">
  <button @click="increment" class="btn btn-success"> + </button>
  <button @click="decrement" class="btn btn-danger"> - </button>
  <button @click="reset" class="btn btn-secondary"> Reset </button>
  <button :disabled="bloquearBoton" @click="agregar" class="btn btn-primary"> ADD </button>
</div>
  <hr>
  {{arrayFavoritos}}
  
 </div>
</template>

<style>
h1 {
  color: royalblue;
}

.positivos {
  color: green;
}
.negativos {
  color: red;
}
.zero {
  color: peru;
}
</style>