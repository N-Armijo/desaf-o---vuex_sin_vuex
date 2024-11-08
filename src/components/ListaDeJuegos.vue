<script setup>
    import { useJuegosStore } from '@/stores/juegosStore'
    import { storeToRefs } from 'pinia'

    const juegosStore = useJuegosStore()
    const { juegos } = storeToRefs(juegosStore)
    const { incrementar, decrementar } = juegosStore 
</script>
<template>
    <div class="row">
        <h2 class="mb-5 text-center">Lista de juegos</h2>
        <div class="col-6 mx-auto">
            <table class="table border border-secondary-subtle text-center">
                <thead>
                    <tr>
                    <th>Codigo</th>
                    <th>Nombre</th>
                    <th>Stock</th>
                    <th>Precio</th>
                    <th>Acciones</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="juego,i in juegos" :key="juego.codigo">
                        <td>{{ juego.codigo }}</td>
                        <td>{{ juego.nombre }}</td>
                        <td>{{ juego.stock }}</td>
                        <td>{{ juego.precio }}</td>
                        <td>
                            <button @click="incrementar(i)" class="btn btn-success fw-bold text-light mx-2">
                            +
                            </button>
                            <button @click="decrementar(i)" class="btn btn-danger fw-bold text-light">-</button>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>