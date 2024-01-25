<template>
    <div class="wrapper_pagination">
        <div 
            class="page"
            v-for="page in totalPage" 
            :key="page"
            :class="{
                'current_page': page === selectPage
            }"
            @click="changePage(page)"
        >
            {{ page }}
        </div>
    </div>
</template>
    
<script>
export default {
    name: 'my-pagination',
    props: {
        totalPage: {
            type: Number,
            required: true
        },
        selectPage: {
            type: Number,
            required: true
        },
    },
    methods: {
        changePage(page) {
            this.$emit('changePage', page)
        }
    }
}
</script>
    
<style>
.wrapper_pagination {
   
    border-radius: 5px;
    height: 40px;
    display: flex;
    column-gap: 5px;
    padding: 5px;
    justify-content: center;
    align-items: center;
}

.page {
    border: 1px solid #00a144;
    border-radius: 5px;
    padding: 5px;
}

.current_page {
    border: 2px solid #00a144;
    border-radius: 5px;
    padding: 5px;
    background-color: #00a14327;
}

</style>