<script setup>
import { ref, computed, onMounted } from 'vue';

import ButtonCounter from './components/ButtonCounter.vue'
import BlogPost from './components/BlogPost.vue';
import BlogPost2 from './components/BlogPost2.vue';
import BlogPostObjetos from './components/BlogPostObjetos.vue'; //cuando es exportacion por defecto va si nllaves
import PaginatePost from './components/PaginatePost.vue';
import LoadingSpinner from './components/LoadingSpinner.vue';

//SLICE
const posts = ref([]);
const postXPage = 10; //inicializar antes del fin
const inicio = ref(0); //hago el inicio reactivo
const fin = ref(postXPage);
//---------------------------------------
const loading = ref(true);

const favorito = ref('');
const cambiarFavorito = (title) => { //recibimos el post y tenemos que hacerlo de manera reactiva
  favorito.value = title
};

//PAGINACION
const next = () => {
  inicio.value = inicio.value + postXPage
  fin.value = fin.value + postXPage
};
const prev = () => {
  inicio.value = inicio.value - postXPage
  fin.value = fin.value - postXPage
};

//onMonted se ejecuta una vez se ha montado nuestro Template
onMounted(async () => {
  loading.value = true
  try {
    const res = await fetch('https://jsonplaceholder.typicode.com/posts') //solo para promesas
    posts.value = await res.json() //formateamos lo recibido a JSON y se devuelve a Post.value
  } catch (error) {
    console.log(error)

  }
  finally {
    setTimeout(() => {
      loading.value = false
    }, 1500);
  }

})
//---------------------------------------------------------------------
//CONSULTA API, lo pasamos al onMounted
//fetch('https://jsonplaceholder.typicode.com/posts')
//  .then(respuesta => respuesta.json())
//  .then((data) => {
//    posts.value = data
//  })
//  .finally(() =>
//    setTimeout(() => {
//      loading.value = false
//    }, 2000),
//  );
//el time out va a ejecutar lo que este dentro de eta funcion despues de 2s

//---------------------------------------------------------------------
//ASYNC Y AWAIT LA MEJOR FORMA:
/*
const fetchData = async() => {
  loading.value = true
  try {
    const res = await fetch('https://jsonplaceholder.typicode.com/posts') //solo para promesas
    posts.value = await res.json() //formateamos lo recibido a JSON y se devuelve a Post.value
  } catch (error) {
    console.log(error)

  }
  finally {
    setTimeout(() => {
      loading.value = false
    }, 1500);
  }
}
*/
//---------------------------------------------------------------------

//Con COMPUTED
const maxLength = computed(() => posts.value.length)


</script>
<template>
  <LoadingSpinner v-if="loading" />
  <div class="container" v-else="">
    <h1>APP</h1>
    <h2>Mis Post Favorito: {{favorito}}</h2>

    <PaginatePost @next="next" @prev="prev" :inicio="inicio" :fin="fin" :maxLength="maxLength" class="mb-2" />
    <!--mb ==> magin-button-->
    <br>
    <!--Recorrer array con v-for en componentes-->
    <BlogPostObjetos v-for="post in posts.slice(inicio, fin)" :key="post.id" class="mb-2" :title="post.title"
      :id="post.id" :body="post.body" @cambiarFavoritoNombre="cambiarFavorito">
      <!--Esto es un evento personalizable o nombre de propiedad-->
      <!--dentro de las comillas es el metodo creado arriba-->
      <!--Con el .slice recorremos el array y le decimos donde empieza y donde acaba-->

    </BlogPostObjetos>
  </div>
</template>


<!--VIDEO 60
-->