<template>
    <div class="container mx-auto w-1/2 py-8">
      <ul
        v-if="errors.length > 0"
        className="mb-4 list-disc list-inside text-sm text-red-600"
      >
        <li v-for="(error, index) in errors" :key="index">
          {{ error }}
        </li>
      </ul>
      <form action="#" class="space-y-6" @submit.prevent="createTodo">
        <div>
          <label for="title" class="block font-semibold">Title</label>
          <input
            type="text"
            v-model="title"
            id="title"
            class="px-2 py-2 w-full shadow rounded mt-2"
          />
        </div>
        <div>
          <label for="description" class="block font-semibold">Description</label>
          <textarea
            v-model="description"
            name="description"
            id="description"
            cols="30"
            rows="10"
            class="px-2 py-2 w-full shadow rounded mt-2"
          ></textarea>
        </div>
        <div>
          <button
            type="submit"
            class="inline-block bg-blue-600 hover:bg-blue-700 text-white rounded px-4 py-2"
          >
            Add To-Do
          </button>
          <span v-show="isLoading">Loading...</span>
        </div>
      </form>
    </div>
  </template>
  
  <script setup>
  const title = ref('')
  const description = ref('')
  const isLoading = ref(false)
  const errors = ref([])
  const router = useRouter()
  
  async function createTodo() {
    isLoading.value = true
    try {
      const post = await useNuxtApp().useFetch(`http://todoapp.vokers.co.zw/api/todos`, {
        method: 'POST',
        body: {
          title: title.value,
          description: description.value,
        },
      })
  
      isLoading.value = false
  
      title.value = ''
      description.value = ''
  
      alert('creating post')
  
      router.push('/')
    } catch (err) {
      console.log(err.data)
      errors.value = Object.values(err.data.errors).flat()
      isLoading.value = false
    }
  }
  </script>