<script>
    export let todo, updateTodo;
</script>

<div>
        <input type="checkbox" checked={todo.isComplete}>
        <input type="text" value={todo.task} on:input={(e) =>
        {
            todo.task = e.currentTarget.value;
            updateTodo(todo)}
        
        }>
        
        <button>Delete</button>
    </div>