<script>
import useApi from "../services/UseApi";
import { defineComponent, onMounted} from 'vue'
import { useRouter } from '#vue-router'

export default defineComponent({
  setup() {
    const { listJoin } = useApi()
    const router = useRouter()

    const listArticle = ref([])
    const titleBlog = "<code/News >"

    const getListArticle = async () => {
      try {
        listArticle.value = await listJoin('posts', 'author');
      } catch (error) {
        console.error(error);
      }
    }

    const handleClick = async (id) => {
      router.push({
        path: `/news/${id}`
      })
    }

    onMounted(() => {
      getListArticle()
    })

    return {
      listArticle,
      titleBlog,
      handleClick
    }
  }

}) 
</script>

<template>
  <div class="sm:w-1/2 w-9/12 mx-auto my-20">
    <h1 class="sm:text-5xl text-4xl font-semibold text-indigo-400 font-mono">{{ titleBlog }}</h1>

    <article class="my-20" v-for="(article, index) in listArticle" :key="index">
      <h2 class="text-4xl font-semibold mb-5 font-mono text-indigo-500 ">{{ article.title }}</h2>
      <p class="mb-5 text-gray-200 font-thin" v-html="article.description.substr(0, 300) + ' ...'"></p>

      <div class="flex sm:justify-end gap-3 mb-4 justify-start ">
        <p class="text-blue-400 font-mono">{{ article.author.name }} |</p>
        <p class="text-blue-400 font-mono">{{ new Date(article.created_at).toLocaleDateString() }}</p>
      </div>

      <button class="bg-red-600 rounded-full w-32 h-8 text-gray-200 font-mono font-bold uppercase" @click="handleClick(article.id)">
        Veja mais >
      </button>
     
    </article>
  </div>
</template>
