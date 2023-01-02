<template>
    <div class="post__item">
        <div>
            <div><strong>Name:</strong>{{ post.title }}</div>
            <div><strong>Desctription:</strong> {{ post.body }}</div>
        </div>
        <div class="post__btns">
            <my-button @click="$emit('remove', post)" class="btn">Delete</my-button>
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
    },
    // methods: {
    // deletePost() {
    //     this.$emit('delete', this.post.id)
    //     console.log("id:", this.post.id);
    // }
    // }

}
</script>

<style scoped>
.post__item {
    display: flex;
    justify-content: space-between;
}
</style>