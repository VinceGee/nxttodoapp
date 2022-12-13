<template>
    <div class="container mx-auto w-1/2 py-8">
        <Title>{{todo.title}} | {{ title }}</Title>
    <h3 class="text-3xl font-bold">
            {{todo.title}}
        </h3>

          <div class="post-meta t ext-gray-700 flex items-center space-x-2">
            <div>{{ format(new Date(props.todo.created_at), 'MMMM dd, yyyy') }}</div>
            <div>&middot;</div>
            <div>{{todo.due_date_time}}</div>
          </div>

          <div class="post-content mt-4">
            {{todo.description}}
          </div>
    </div>
</template>

<script setup>
    import { format } from 'date-fns' 

    const title = useState('title', () => 'ToDo App')
    const { data: todo } = await useFetch(`http://todoapp.vokers.co.zw/api/todos/${route.params.id}`)

</script>