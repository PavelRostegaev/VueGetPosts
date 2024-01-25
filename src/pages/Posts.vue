<template>
    <div>
        <h1>Страница с постами</h1>
        <my-button
            style="margin-top: 15px;"
        >
            <router-link 
                to="/"
                style="text-decoration: none; color: black;"
            >На главную
            </router-link>
        </my-button>
        
        <div class="wrapper_btns">
            <my-button
                @click="displayModal"
            >Создать пост</my-button>
            <my-select
                v-model="selectedSort"
                :options="sortOption"
            />
        </div>
        
        <my-modal v-model:visible="visibleModal">
            <post-form
                @createdPost="pushPost"
                @closeModal="() => this.visibleModal = false"
            />
        </my-modal>

        <my-input
            v-model:value="searchValue"
            placeholder="Поиск..."
            style="margin-bottom: 15px;"
        ></my-input>

        <div v-if="!isPostLoading">
            <post-list
                :postList="sortedAndSearched"
                @removePost="deletePost"
            />
            <my-pagination
                :totalPage="totalPage"
                :selectPage="selectPage"
                @changePage="changePage"
            />
        </div>
        
        <h3 v-else>Загрузка постов...</h3>

    </div>
</template>
    
<script>
import PostList from '@/components/PostList.vue'
import PostForm from '@/components/PostForm.vue'
import axios from 'axios'

export default {
    components: {
        PostList, PostForm
    },
    data() {
        return {
            postList: [],
            visibleModal: false,
            isPostLoading: false,
            selectedSort: '',
            searchValue: '',
            selectPage: 1,
            limit: 10,
            totalPage: 0,
            sortOption: [
                {value: 'title', name: 'По названию'},
                {value: 'body', name: 'По содержимому'},
            ]
        }
    },
    methods: {
        pushPost(newPost) {
           this.postList.push(newPost)
           this.visibleModal = false
        },
        deletePost(post){
            this.postList = this.postList.filter(p => p.id !== post.id )
        },
        displayModal() {
            this.visibleModal = true
        }, 
        changePage(page){
            this.selectPage = page
            this.fetchPosts()
        },
        async fetchPosts() {
            try {
                this.isPostLoading = true
                setTimeout(async () => {
                    const response = await axios.get(`https://jsonplaceholder.typicode.com/posts`, {
                        params: {
                            _page: this.selectPage,
                            _limit: this.limit,
                        }
                    })
                    this.totalPage = Math.ceil(response.headers['x-total-count'] / this.limit)
                    this.postList = response.data
                    this.isPostLoading = false
                }, 600)
            } catch (e) {
                console.log('Ошибка', e.text);
            }
        }
    },
    mounted() {
        this.fetchPosts()
    },
    computed: {
        sortedPosts() {
            return [...this.postList].sort((post1, post2) => 
             post1[this.selectedSort]?.localeCompare(post2[this.selectedSort])
            )
        },
        sortedAndSearched() {
            return this.sortedPosts.filter(post => post.title.toLowerCase().includes(this.searchValue))
        }
    },
    watch: {
       
    }
}
    
</script>
    
<style>
.wrapper_btns {
    display: flex;
    justify-content: space-between;
    margin: 15px 0;
}

</style>