<template>
    <div class="app">
        <h1>Posts page</h1>
        <div class="app__btns">
            <my-button @click="showDialog" class="createPost">Create post</my-button>
            <my-select v-model="selectedSort" :options="sortOptioins" />
        </div>
        <my-dialog v-model:show="dialogVisible">
            <post-form @create="createPost" />
        </my-dialog>
        <post-list @remove="removePost" v-bind:posts="posts" v-if="!isPostsLoading" />
        <div v-else>Loading...</div>
    </div>
</template>

<script>
import axios from 'axios'
import PostForm from "@/components/PostForm.vue"
import PostList from "./components/PostList.vue"
import MyButton from './components/UI/MyButton.vue';
import MySelect from './components/UI/MySelect.vue';

export default {
    components: {
        PostList, PostForm,
        MyButton, MySelect
    },
    data() {
        return {
            posts: [],
            dialogVisible: false,
            isPostsLoading: false,
            selectedSort: '',
            sortOptioins: [
                { value: 'title', name: 'By title' }, { value: 'body', name: 'By description' }
            ]
        };
    },
    methods: {
        createPost(post) {
            this.posts.push(post);
            this.dialogVisible = false;

        },
        removePost(post) {
            this.posts = this.posts.filter(p => p.id !== post.id)
        },
        showDialog() {
            this.dialogVisible = true;

        },

        async fetchPosts() {
            try {
                this.isPostsLoading = true;
                const response = await axios.get('https://jsonplaceholder.typicode.com/posts/?_limit=10')
                this.posts = response.data;

            } catch (e) {
                alert("get post errror!")
            } finally {
                this.isPostsLoading = false;
            }

        },


        // deletePost(id) {
        //     console.log('posyitem id:', id);
        //     this.posts = this.posts.filter((post) => post.id != id)
        // }
        // inputTitle(event) {
        //     this.title = event.target.value
        // },

    },

    // hooks
    mounted() {
        this.fetchPosts()
    }
};
</script>

<style scoped>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

.app {
    padding: 20px;
}

.app__btns {
    display: flex;
    justify-content: space-between;
}

.createPost {
    margin: 15px 0;
}
</style>
