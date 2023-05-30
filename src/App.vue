<script setup>
import { reactive } from "vue";

const estado = reactive({
    valor_um: "",
    valor_dois: "",
    operacao: "+",
    resultado: 0,
});

function getResultado() {
  if (estado.operacao == "+" && estado.valor_um !== "" && estado.valor_dois !== "") {
        return `A soma de ${estado.valor_um} + ${estado.valor_dois} e igual a ${estado.valor_um + estado.valor_dois}`;
    } else if (estado.operacao == "-" && estado.valor_um !== "" && estado.valor_dois !== "") {
        return `A subtração de ${estado.valor_um} - ${estado.valor_dois} e igual a ${estado.valor_um - estado.valor_dois}`;
    } else if (estado.operacao == "*" && estado.valor_um !== "" && estado.valor_dois !== "") {
        return `A multiplicação de ${estado.valor_um} * ${estado.valor_dois} e igual a ${estado.valor_um * estado.valor_dois}`;
    } else if (estado.operacao == "/" && estado.valor_um !== "" && estado.valor_dois !== "") {
        return `A divisão de ${estado.valor_um} / ${estado.valor_dois} e igual a ${estado.valor_um / estado.valor_dois}`;
    }
}
</script>

<template>
    <div class="container pt-5 bg-light">
        <h1 class="text-center pb-2">Calculadora Aritmética</h1>
        <div class="separador d-flex gap-2">
            <input
                type="number"
                class="w-50 text-center"
                placeholder="Informa um número"
                v-model="estado.valor_um"
            />
            <select @change="evento => estado.operacao = evento.target.value" class="form-control w-25 text-center">
                <option value="+">+</option>
                <option value="-">-</option>
                <option value="*">*</option>
                <option value="/">/</option>
            </select>
            <input
                type="number"
                class="w-50 text-center"
                placeholder="Informa um segundo número"
                v-model="estado.valor_dois"
            />
        </div>
        <span class="d-flex pt-3 fs-1 justify-content-center">{{
            getResultado()
        }}</span>
    </div>
</template>

<style scoped></style>
