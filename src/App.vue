<script setup>
    import { reactive } from 'vue';
    import Cabecalho from './components/Cabecalho.vue';
    import Formulario from './components/Formulario.vue';
    import Resultado from './components/Resultado.vue';

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
        <Cabecalho/>
        <Formulario :pegarResultado="getResultado" :pegarNum1="evento => estado.num1 = evento.target.value" :pegarNum2="evento => estado.num2 = evento.target.value" :pegarOperacao="evento => {estado.operacao = evento.target.value; getResultado();}"/>
        <Resultado :mostrarResultado="estado.resultado"/>
    </div>
</template>

<style scoped>
</style>