<template>
   <div>
        <h2>Данное приложение было создано для освоения возможностей фреймворка Vue 3</h2>
        <my-button
            style="margin-top: 15px;"
        >
            <router-link 
                to="posts"
                style="text-decoration: none; color: black;"
            >Перейти к самому проекту
            </router-link>
        </my-button>
        <my-about/>
    </div>
    
</template>
    
<script>
    import MyAbout from '@/components/MyAbout.vue'

export default({
    components: {
        MyAbout
    }
})
</script>
    
<style>
* {
padding: 0;
margin: 0;
box-sizing: border-box;
}

.app {
    padding: 15px;
}
</style>