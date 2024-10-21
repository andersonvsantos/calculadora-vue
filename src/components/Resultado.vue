<script setup>
    const props = defineProps(['mostrarResultado']);
</script>

<template>
    <div class="row mt-4">
        <div class="col">
            <h2>Resultado</h2>
            <span>{{ props.mostrarResultado }}</span>
        </div>
    </div>
</template>