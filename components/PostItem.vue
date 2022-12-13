<template>
    <div class="post-container py-8">
        <h3 class="text-3xl font-bold">
            <NuxtLink to="`todos/{{props.todo.id}}`" >{{ props.todo.title }}</NuxtLink>
        </h3>  
          <div class="post-meta text-gray-700 flex items-center space-x-2">
            <div>{{ props.todo.created_at }}</div>
            <div>&middot;</div>
            <div>Due: {{ props.todo.due_date_time }}</div>
          </div>
            <div class="post-preview leading-relaxed mt-4">
                {{ props.todo.description }}  
            </div>
            <div class="mt-4">
                <NuxtLink to="`todos/${{props.todo.id}}`" class="bg-blue-700 hover:bg-blue-800 text-white rounded inline-block px-4 py-2"> Todo Details</NuxtLink>
            </div>

          
    </div>
</template>

<script setup>
import { format } from 'date-fns'

const props = defineProps({
    todo: Object,
})

</script>
