<script setup>
import ButtonCounter from './components/ButtonCounter.vue'
import BlogPost from './components/BlogPost.vue'; //cuando es exportacion por defecto va si nllaves

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
    </div>
</template>
