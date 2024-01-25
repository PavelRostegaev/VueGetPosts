<template>
    <div>
        <div class="post">
            <div class="block_info">
                <div><strong>Id: </strong>{{ post.id }}</div>
                <div><strong>Название: </strong>{{ post.title }}</div>
                <div><strong>Описание: </strong>{{ post.body }}</div>
            </div>
                <div class="block_btn">
                <my-button
                    @click="this.$emit('removePost', post)"
                >Удалить
                </my-button>
            </div>
        </div> 
    </div>

</template>
    
<script>
export default {     
    props: {
        post: {
            type: Object,
            required: true,
        }
    }
}
</script>
    
<style>
.post {
    border: 2px solid #00a144;
    border-radius: 5px;
    padding: 10px;
    margin-bottom: 10px;
    display: flex;
    flex-direction: center;
    justify-content: space-between;
}   
</style>