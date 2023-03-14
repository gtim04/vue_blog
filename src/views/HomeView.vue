<template>
  <div class="home">
    <h1>Home</h1>
    <div v-if="error">{{ error }}</div>
    <div v-if="posts.length">
        <PostList v-if="showPosts" :posts="posts" />
    </div>
    <div v-else>Loading...</div>
    <!-- <button @click="showPosts = !showPosts">toggle post</button>
    <button @click="posts.pop()">delete a post</button> -->
  </div>
</template>

<script>
import PostList from '../components/PostList.vue'
import getPosts from '../composables/getPosts'

export default {
    name: 'Home',
    components: { PostList },
    setup() {
        // const showPosts = ref(true)
        const showPosts = true

        const { posts, error, load } = getPosts()

        load()

        return { posts , showPosts, error}
    }
}
</script>

<style>

</style>