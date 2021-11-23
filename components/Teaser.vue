<template>
    <div class="text-center bg-white rounded-xl shadow-md">
      <h1 class="blog-title">
        {{teaser.title}}
      </h1>
      <div class="py-8 px-8 mx-auto space-y-2 sm:py-4 sm:flex sm:items-center sm:space-y-0 sm:space-x-6 md:py-4 md:flex md:items-center md:space-y-0 md:space-x-6">
        <nuxt-img
          provider="imgix"
          :src="teaser.heroimage.url"
          class="lg:w-3/5 md:w-1/2 sm:w-1/2 w-full"
          sizes="xl:60vw, lg:60vw, md:50vw, sm:90vw, xs:90vw"
          fit="crop"
          :modifiers="{ crop: 'faces,edges', ar: '1.8:1', ch: 'dpr,width', auto: 'format,compress'}"
        />
        <div class="text-center space-y-2">
          <div class="space-y-0.5">
          <p class="blog-description inline">{{teaser.content}}</p> 
          </div>
        </div>
      </div>
    </div>
</template>

<script>
import getTeaser from '../apollo/queries/getTeaser.gql'

export default {
  apollo: {
    teaser: {
      prefetch: true,
      query: getTeaser
    }
  },
};
</script>