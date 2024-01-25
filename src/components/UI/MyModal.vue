<template>
    <div 
        v-if="visible" 
        @click.stop="hideModal"
        class="wrapper_modal"
    >
        <div 
            @click.stop
            class="modal"
        >
            <slot></slot>
        </div>
    </div>    
</template>
    
<script>
export default {
    name: 'my-modal',
    props: {
        visible: {
            type: Boolean,
            default: false,
        }
    },
    methods: {
        hideModal() {
            this.$emit('update:visible', false)
        }
    }
}
</script>

    
<style>
.wrapper_modal {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: #00000080;
    display: flex;
    justify-content: center;
    align-items: center;
}

.modal {
    padding: 15px;
    background-color: #ffffff;
    border-radius: 10px;
    min-width: 350px;
    height: 270px;
}
</style>