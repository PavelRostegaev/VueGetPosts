<template>
    <button class="btn">
        <strong><slot></slot></strong>
    </button>
</template>
    
<script>
export default {
    name: 'my-button'
}
</script>

<style>
.btn {
    border: 1px solid #00a144;
    border-radius: 5px;
    padding: 10px;
    min-width: 100px;
    background-color: #3ba1001e;
}

</style>