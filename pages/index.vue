<template>
    <div class="container">
        <div class="d-flex justify-content-between">
            <div>
                <h3 class="mt-4">Articles</h3>
            </div>
            <div>
                 <NuxtLink to="blog/add" type="button" class="btn btn-info mt-4 text-white">Add Article</NuxtLink>
            </div>     
        </div>
        <div class="row mt-5 w-100">
            <Card v-for="article in articles.data" :key="article.id" :article="article" />
        </div>
    </div>
</template>
<script>
export default {
    layout: 'blog',
    buildModules: [
        '@nuxtjs/moment'
    ],
    moment: {
        locales: ['th']
    },
    async asyncData({ $axios }) {
        const articles = await $axios.$get("/api/articles");
        return { articles };
    },
    head() {
        return {
        title: 'Nuxt Fetch API'
        };
    }
};
</script>
<style scoped>

</style>