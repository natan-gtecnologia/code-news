<!-- <template>
  <div class="w-1/2 mx-auto my-20">
    <div class="mt-20 mb-10">
      <h2 class="text-5xl font-semibold mb-5 text-indigo-500 font-mono">
        {{ article?.title }}
      </h2>
      <p class="mb-5 text-gray-200 font-thin">{{ article?.descricao }}</p>

      <div class="flex items-end flex-col font-mono">
        <p class="text-blue-400">{{ article?.autor?.nome }}</p>
        <span class="text-gray-200 text-sm">
          {{ article?.autor?.formacao }}</span
        >
        <span class="text-gray-200 text-sm"> {{ article?.autor?.nivel }}</span>
      </div>
    </div>

    <NuxtLink to="/">
        <button class="bg-red-600 rounded-full w-28 h-7 text-gray-200 font-thin">
          Voltar 
        </button>
      </NuxtLink>
  </div>
</template>

<script setup>
// import api from "../../services/api";
import { ref, onMounted } from "vue";
import { useRoute } from "vue-router";
import useApi from "services/UseApi";

const article = ref({});
const route = useRoute();

const { getById } = useApi()

async function getArticle() {
  try {
    article.value = await getById('posts', route.params.id);
  } catch (error) {
    console.error(error);
  }
}

onMounted(() => {
  getArticle();
});
</script> -->

<template>
  <div>
    oi
  </div>

</template>
