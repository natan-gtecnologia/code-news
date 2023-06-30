<template>
  <div class="w-1/2 mx-auto my-20">
    <div class="mt-20 mb-10">
      <h2 class="text-5xl font-semibold mb-5 text-indigo-500">{{ article.titulo }}</h2>
      <p class="mb-5 text-gray-200">{{ article.descricao }}</p>
      
      <div class="flex items-end flex-col">
        <p class="text-blue-400 ">{{ article.autor?.nome }}</p>
        <span class="text-gray-200 text-sm"> {{ article.autor?.formacao }}</span>
        <span class="text-gray-200 text-sm"> {{ article.autor?.nivel }}</span>
      </div>
    </div>

    <button class="bg-red-600 rounded-full w-28 h-7 text-gray-200">
      <NuxtLink to="/"> Voltar </NuxtLink>
    </button>
  </div>

</template>

<script>
import api from "../../services/api";
export default {
  data() {
    return {
      article: {},
    };
  },
  methods: {
    async getArticle() {
      try {
        const {data} = await api.get(`noticias/${this.$route.params.id}`);
        this.article = data;
      } catch (error) {
        console.error(error);
      }
    },
  },

  mounted() {
    this.getArticle();
  },
};
</script>
