<script setup>
    const props = defineProps(['display', 'resultado', 'error', 'back'])
</script>
<template>
    <div class="calculator-display text-end">
        <div class="display text-break mb-4">
            <h1 class="text-light" :class="{ 'small-text': props.display.length >= 12 }">{{ props.display }}|</h1>
        </div>
    </div>
    <div class="calculator-result d-flex justify-content-end text-break mt-4">
        <h2 class="text-secondary fw-normal">{{ props.resultado }}</h2>
    </div>
    <div class="calculator-back d-flex justify-content-end mt-2 mb-3">
        <button @click="props.back" class="btn">
            <i class="bi bi-x-circle fs-5 --green"></i>
        </button>
    </div>
    <div class="calculator-msg-error">
        <h3 class="fs-5 text-white text-center">{{ props.error }}</h3>
    </div>
</template>

<style scoped>

/*Classe para diminuir a fonte os valores exibido no display*/
.small-text {
    font-size: 26px;
    transition: all .3s;
}

.calculator-display {
    height: 68px;
    overflow-y: scroll
}

::-webkit-scrollbar {
    width: 0px;
}

.calculator-result {
    margin-right: 13px;
}

.calculator-back {
    border-bottom: 1px solid #6c757d;
}

.--green {
    color: greenyellow !important;
}

</style>