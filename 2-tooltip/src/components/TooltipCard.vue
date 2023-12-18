<template>
    <div class="tooltip" :style="coordinates"><slot></slot></div>    
</template>

<script>
    export default {
        props: ['coordinates']
    }
</script>

<style scoped>
    .tooltip {
        position: absolute;
        top: 0%;
        left: 0%;
        min-height: 30px;
        min-width: 200px;
        background-color: rgba(0,0,0, 0.4);
        color: #f4f4f4;
        padding: 1rem;
        backdrop-filter: blur(15px);
        border-radius: 4px;
        font-weight: bold;
        pointer-events: none;
    }
</style>