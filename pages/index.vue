<template>
      <div class="flex flex-col justify-center items-center w-full h-full">

            <h1 class="font-extrabold text-6xl py-20">HOME</h1>
            <hr/>
            <button @click="fetchdata" class="w-24 h-auto bg-blue-500 text-white rounded-xl">check here to fetch</button>
            <h3 class="py-20 text-2xl">ID : {{ product.id }}</h3>
            <img :src="product.thumbnail" alt="">
      </div>
</template>

<script setup >
const product = ref({
      id: 0
})

async function fetchdata() {
      const { data, error , pending } = await useFetch(`https://dummyjson.com/products/1`,{
            key: 'data',
      })
      product.value = data.value
}

</script>

<style>

</style>