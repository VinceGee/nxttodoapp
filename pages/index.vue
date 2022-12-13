<template>
    <Title>Home | {{ title }}</Title>

    <div class="container mx-auto w-1/2 py-8 divide-y space-y-8 divide-gray-300">
        <PostItem v-for="todo in todos" :key="todo.id" :todo="todo"/>
    </div>
</template>

<script setup>
    const title = useState('title', () => 'ToDo App')
    const { data } = await useFetch('http://todoapp.vokers.co.zw/api/todos')
    const todos = data.value.data
</script>