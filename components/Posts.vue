<template>
    <div class="flex flex-wrap">
      <div v-for="allPost in allPosts" :key="allPost.id" v-bind:allPost="allPost" class="p-4 lg:w-1/3 md:w-1/2 sm:w-full">
        <h2>{{allPost.title}}</h2>
        <nuxt-img
          provider="imgix"
          :src="allPost.heroimage.url"
          sizes="xl:30vw, lg:40vw, md:90vw, sm:90vw, xs:90vw"
          fit="crop"
          loading="lazy"
          :modifiers="{ crop: 'faces,edges', ar: '1.8:1', ch: 'dpr,width', auto: 'format,compress'}"
        />
        <p>{{allPost.content}}</p>
      </div>
    </div>
</template>

<script>
import getPosts from '../apollo/queries/getPosts.gql'

export default {
  apollo: {
    allPosts: {
      prefetch: true,
      query: getPosts
    }
  },
};
</script>