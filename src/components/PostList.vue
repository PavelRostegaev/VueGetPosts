<template>
    <div class="wrapper_list">
        <div v-if="postList.length === 0">
            <h3
                style="color: brown;"
            >Список постов пуст</h3>
        </div>
        <div v-else>
            <h3>Список постов</h3>
            <transition-group name="post-list">
                <post-item
                    v-for="post in postList"
                    :post="post"
                    :key="post.id"
                    @removePost="$emit('removePost', post)"
                />
            </transition-group>
        </div>
    </div>
</template>
    
<script>
import PostItem from '@/components/PostItem.vue'

export default {
    components: {PostItem}, 
    props: {
        postList: {
            type: Array,
            required: true,
        }
    }
}
</script>
    
<style scoped>
 .post-list-item {
  display: inline-block;
  margin-right: 10px;
}
.post-list-enter-active,
.post-list-leave-active {
  transition: all .5s ease;
}
.post-list-enter-from,
.post-list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}
.post-list-move {
  transition: transform 0.4s ease;
}
</style>