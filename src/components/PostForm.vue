<template>
    <form class="post__form" @submit.prevent>
        <h4>Create post</h4>
        <div class="input__post">
            <my-input v-model="post.title" class="input" type="text" placeholder="Type post name" />
            <my-input v-model="post.body" class="input" type="text" placeholder="Type post body" />
        </div>
        <my-button @click="createPost">Add</my-button>
    </form>
</template>

<script>
export default {
    data() {
        return {
            post: {
                title: '',
                body: ''
            }
        }
    },
    methods: {
        createPost() {
            // const newPost = {
            //     id: Date.now(),
            //     title: this.post.title,
            //     body: this.post.body
            // }
            this.post.id = Date.now()
            // генеруємо подію
            this.$emit('create', this.post)
            this.post = { title: '', body: '' }
        }
    }
}


</script>

<style scoped>
.post__form {
    margin-bottom: 35px;
    display: flex;
    flex-direction: column;

}


.input:first-child {
    margin-top: 20px;
    margin-right: 20px;
}

.post__form button {
    align-self: flex-start;
}
</style>