<script>
import useApi from "../services/UseApi";
// import api from "../services/api";
import { defineComponent, onMounted} from 'vue'

export default defineComponent({
  setup() {
    const { list } = useApi()

    const listArticle = ref([])
    const titleBlog = "<code/News >"

    const getListArticle = async () => {
      try {
        listArticle.value = await list('posts');
      } catch (error) {
        console.error(error);
      }
    }

    const handleClick = async (id) => {
      this.$router.push({
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
  <div class="w-1/2 mx-auto my-20">
    <h1 class="text-5xl font-semibold text-indigo-400 font-mono">{{ titleBlog }}</h1>

    <article class="my-20" v-for="(article, index) in listArticle" :key="index">
      <h2 class="text-4xl font-semibold mb-5 font-mono text-indigo-500 ">{{ article.title }}</h2>
      <p class="mb-5 text-gray-200 font-thin">{{ `${article.description.substr(0, 300)}` + " ..." }}</p>
      <!-- <p class="text-blue-400 flex justify-end font-mono">{{ article.autor.nome }}</p> -->

      <button class="bg-red-600 rounded-full w-28 h-7 text-gray-200 font-thin" @click="handleClick(article.id)">
        Veja mais
      </button>
     
    </article>
  </div>
</template>
