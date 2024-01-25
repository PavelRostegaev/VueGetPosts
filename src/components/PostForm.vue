<template>
    <form 
        class="wrap_form" 
        @submit.prevent
    >
        <h3>Создание поста</h3>
        <my-input 
            v-model:value="post.title" 
            placeholder="Название"
        />
        <my-input  
            v-model:value="post.body" 
            placeholder="Описание"
        />
        <my-button 
            class="btn" 
            @click="createPost"
        >Добавить
        </my-button>
        <my-button 
            class="btn" 
            @click="closeModal"
        >Закрыть
        </my-button>
    </form>
</template>
    
<script>
import MyButton from '@/components/UI/MyButton.vue'

export default {
    components: {
        MyButton
    },
    data() {
        return {
            post: {
                title: '',
                body: '',
            },
        }
    },
    methods: {
        createPost() {
            if ( this.post.title != '' && this.post.body != '') {
                this.post.id = Date.now();
                this.$emit('createdPost', this.post);
                this.post = {
                    title: '',
                    body: ''
                }
            }
        },
        closeModal() {
            this.$emit('closeModal', false);
        }
    }
}
</script>
    
<style>
.wrap_form {
    display: flex;
    flex-direction: column;
    row-gap: 10px;
    margin-bottom: 15px;
    padding: 10px;
    border: 2px solid #00a144;
    border-radius: 5px;
}

</style>