<script setup>
    const props = defineProps(['tarefasPendentes'])
</script>

<template>
    <header class="p-5 mb-4 mt-4 rounded-3">
        <h1>Minhas tarefas</h1>
        <p>
            Você possui {{ props.tarefasPendentes }} tarefas pendentes.
        </p>
    </header>
</template>

<style scoped>
    header {
        border-radius: 8px;
        background-color: rgb(28, 47, 95);
        color: white;
    }
</style>