<template>
    <div v-if="posts?.length > 0">
        <h3>Post list:</h3>
        <post-item v-for="post in posts" class="post" :post="post" :key="post.id" @remove="$emit('remove', post)" />
    </div>
    <div v-else class="notPosts">There are not posts</div>
</template>

<script>
import PostItem from "./PostItem"
export default {
    components: { PostItem },
    props: {
        posts: {
            type: Array,
            required: true
        }
    }
}
</script>

<style scoped>
.post {
    padding: 15px;
    border: 2px solid teal;
    margin-bottom: 10px;
}

.notPosts {
    font-size: 30px;
    color: red;
}
</style>