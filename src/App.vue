<script setup>
    import { reactive } from 'vue';

    const estado = reactive({
        operacao: 'somar',
        num1: 0,
        num2: 0,
        resultado: ''
    });

    const somar = () => {
        estado.resultado = parseInt(estado.num1) + parseInt(estado.num2);
    }

    const subtrair = () => {
        estado.resultado = parseInt(estado.num1) - parseInt(estado.num2);
    }

    const dividir = () => {
        estado.resultado = parseInt(estado.num1) / parseInt(estado.num2);
    }

    const multiplicar = () => {
        estado.resultado = parseInt(estado.num1) * parseInt(estado.num2);
    }

    const getResultado = () => {
        const { operacao } = estado;

        switch (operacao) {
            case 'somar':
                return somar()
            case 'subtrair':
                return subtrair()
            case 'dividir':
                return dividir()
            default:
                return multiplicar()
        }
    }
</script>

<template>
    <div class="container text-center">
        <header class="mt-3 mb-3">
            <h1>Calculadora</h1>
        </header>
        <form @submit.prevent="getResultado">
            <div class="row">
                <div class="col-5">
                    <input @change="getResultado" @keyup="evento => estado.num1 = evento.target.value" type="number" class="form-control">
                </div>
                <div class="col-5">
                    <input @change="getResultado" @keyup="evento => estado.num2 = evento.target.value" type="number" class="form-control">
                </div>
                <div class="col-2">
                    <select @change="evento => {estado.operacao = evento.target.value; getResultado()}" class="form-control text-center" id="select">
                        <option value="somar" class="option">+</option>
                        <option value="subtrair" class="option">-</option>
                        <option value="dividir" class="option">/</option>
                        <option value="multiplicar" class="option">*</option>
                    </select>
                </div>
            </div>
        </form>
        <div class="row mt-4">
            <div class="col">
                <h2>Resultado</h2>
                <span>{{ estado.resultado }}</span>
            </div>
        </div>
    </div>
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
