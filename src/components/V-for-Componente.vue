<script setup>
import ButtonCounter from './components/ButtonCounter.vue'
import BlogPost from './components/BlogPost.vue';
import BlogPost2 from './components/BlogPost2.vue';
import BlogPostObjetos from './components/BlogPostObjetos.vue'; //cuando es exportacion por defecto va si nllaves
import { ref } from 'vue';

const posts = ref([
    { title: 'post 9', id: 9, body: 'descripcion9' },
    { title: 'post 10', id: 10, body: 'descripcion10' },
    { title: 'post 11', id: 11, body: 'descripcion11' },
    { title: 'post 12', id: 12 },
])
</script>
<template>
    <div class="container">
        <h1>APP</h1>
        <ButtonCounter></ButtonCounter>
        <ButtonCounter></ButtonCounter>
        <BlogPost title="post 1" id="1" body="Descripcion 1" colorText="primary" />
        <!--a estos componentes se les pueden mandar PROPS o Accesorios-->
        <BlogPost title="post 2" id="2" body="Descripcion 2" colorText="secondary" />
        <BlogPost title="post 3" id="3" body="Descripcion 3" colorText="success" />
        <BlogPost title="post 4" id="4" body="Descripcion 4" colorText="danger" />
        <br>
        <!--Props2-->
        <BlogPost2 title="post 5" id="5" body="Descripcion 5" colorText="primary" />
        <BlogPost2 title="post 6" id="6" body="Descripcion 6" colorText="warning" />
        <BlogPost2 title="post 7" id="7" body="Descripcion 7" colorText="success" />
        <BlogPost2 title="post 8" id="8" body="Descripcion 8" colorText="danger" />
        <br>
        <!--Recorrer array con v-for en componentes-->
        <BlogPostObjetos v-for="post in posts" :key="post.id" :title="post.title" :id="post.id" :body="post.body">

        </BlogPostObjetos>
    </div>
</template>
