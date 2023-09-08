<script>
    import {onMount} from 'svelte';
    import supabase from "$lib/db";
    import Todo from '$lib/Todo.svelte';

    let todos = [];

    onMount(async () => {
        let {data,  error} = await supabase
            .from('todosNew')
            .select('*');
            todos = data;
            // console.table(todos);
    })

    const updateTodo = async (todo) => {
        let {data, error} = await supabase
            .from('todosNew')
            .update({task: todo.task, isComplete: !todo.isComplete})
            .eq('id', todo.id);
            console.log(data);
        console.table(todo);
    }
</script>

{#each todos as todo}
<Todo {todo} {updateTodo}/>
    {:else}
    <p>No todos found boss!!</p>
{/each}
