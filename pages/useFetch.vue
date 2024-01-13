<template>
      <div class="flex flex-col justify-center items-center w-full h-full">

            <h1 class="font-extrabold text-4xl py-20">USE_FETCH</h1>
            <button @click="fetchdata" class="w-auto h-10 bg-blue-500 text-white rounded-xl">ReFetch</button>
            <h3 class="py-20  text-2xl">ID :  {{ product.id }}</h3>
            <img :src="product.thumbnail" alt="">
      </div>
</template>

<script setup >
const product = ref()

const cache = useNuxtData('data')
product.value = cache.data.value

async function fetchdata() {
      const { data, error , pending } = await useFetch(`https://dummyjson.com/products/10`,{
            key: 'data',
            default: ()=> cache.data.value,
      })
      product.value = data.value
}

</script>