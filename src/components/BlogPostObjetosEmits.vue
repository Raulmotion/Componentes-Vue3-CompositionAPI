<script setup>
//defineProps(["title", "id", "body", "colorText"]) //recibo el props tittle y recibirlo con la interpolacion abajo en el template
defineProps({
    title: String, //puede ser String, Number, Array, Boolean, Object, Date, Function, Symbol
    id: Number,
    body: {
        type: String,
        default: "Sin descripcion",
    }
})
</script>
<template>
    <div class="card">
        <div class="card-body">
            <h5 class="card-title">{{id}} - {{title}}</h5>
            <p>{{body}}</p>
            <button @click="$emit('cambiarFavoritoNombre', title)" class="btn btn-outline-primary">
                favorito
            </button>
            <!--usamos emit para usar el argumento cambiarFavorito de app.vue que es donde lo hemos nombrado-->
            <!--le pasamosel titulo como segundo argumento-->

        </div>
    </div>
</template>
