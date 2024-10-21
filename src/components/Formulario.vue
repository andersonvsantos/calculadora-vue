<script setup>
    const props = defineProps(['pegarResultado', 'pegarNum1', 'pegarNum2', 'pegarOperacao']);
</script>

<template>
    <form @submit.prevent="props.pegarResultado">
        <div class="row">
            <div class="col-5">
                <input @change="props.pegarResultado" @keyup="props.pegarNum1" type="number" class="form-control">
            </div>
            <div class="col-5">
                <input @change="props.pegarResultado" @keyup="props.pegarNum2" type="number" class="form-control">
            </div>
            <div class="col-2">
                <select @change="props.pegarOperacao" class="form-control text-center" id="select">
                    <option value="somar" class="option">+</option>
                    <option value="subtrair" class="option">-</option>
                    <option value="dividir" class="option">/</option>
                    <option value="multiplicar" class="option">*</option>
                </select>
            </div>
        </div>
    </form>
</template>

<style scoped>
    #select {
        background-color: rgb(38, 41, 228);
        color: white;
        border: none;
    }
    .option {
        background-color: rgb(209, 215, 218);
    }
</style>