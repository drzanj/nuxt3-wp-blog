<script lang="ts" setup>
import useWpApi from "~~/composables/useWpApi";

useHead({
  title: "Home",
  meta: [
    {
      name: "description",
      content: "Home",
    },
  ],
  titleTemplate: "Elon's Blog - %s",
});
const { data: blogs, refresh, error } = await useWpApi().getPosts();
</script>
<template>
  <main>
    <PageHeader>
      <div class="flex items-center flex-wrap">
        
      </div>
    </PageHeader>

    <!-- Blog Section Starts -->
    <section class="blogs">
      <div class="container py-10">
        <div class="grid sm:grid-cols-3 gap-10">
          <BlogGrid
            v-for="blog in blogs"
            :key="blog.id"
            :title="blog.title.rendered"
            :image="blog._embedded['wp:featuredmedia'][0]?.source_url"
            :excerpt="blog.excerpt.rendered"
            :slug="blog.slug"
          ></BlogGrid>
        </div>
      </div>
    </section>
    <!-- Blog Section Ends  -->
  </main>
</template>

<style>
.hero__title {
  @apply text-4xl font-bold;
}
.hero__des {
  @apply text-xl;
}
</style>
