<template>
    <div>
        <h2>Witaj {{ email }}
        <button @click="$emit('logout')" class="float-right  button-outline button">Wyloguj</button>
        </h2> </div>
</template>

<script>
    export default {
        props: ['email']
    }
</script>
