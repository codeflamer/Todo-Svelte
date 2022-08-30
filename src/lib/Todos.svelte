<script>
    import Todo from "./Todo.svelte";
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();

     export let todos=[];
     export let presentActive = {};
     const forward = (event) =>{
        dispatch("edit",{
            id:event.detail.id
        })
     }

     const forwardFinishEdit = (event) =>{
        dispatch("finishEdit",{
            id:event.detail.id,
            content:event.detail.content
        })
     }

     const handleDelete = (event) =>{
        dispatch("delete",{
            id:event.detail.id
        })
     }

     const handleCompleted = (event) =>{
        dispatch("completed",{
            id:event.detail.id
        })
     }

     const handleActive = (event) =>{
        dispatch("active",{
            id:event.detail.id
        })
     }

</script>

<section>
   
   <div class="todo-container">
       {#if presentActive.name === "All"}
            <h4>{todos.length} todos created.</h4>
            {#each todos as todo}
                <Todo content={todo.content} 
                    id={todo.key} 
                    edit={todo.edit} 
                    status={todo.status}
                    on:edit={forward} 
                    on:finishEdit={forwardFinishEdit} 
                    on:delete={handleDelete} 
                    on:completed={handleCompleted}
                    on:active={handleActive}
                />
            {:else}
                <h2 style="margin-top:10px">Todo List is empty</h2>
            {/each}

        {:else if presentActive.name === "Active"}
            <h4>{todos.filter(todo => todo.status === "active").length} out of {todos.length} todos active.</h4>
            {#each todos.filter(todo => todo.status === "active") as todo}
                <Todo content={todo.content} 
                    id={todo.key} 
                    edit={todo.edit} 
                    status={todo.status}
                    on:edit={forward} 
                    on:finishEdit={forwardFinishEdit} 
                    on:delete={handleDelete} 
                    on:completed={handleCompleted}
                    on:active={handleActive}
                />
            {:else}
                <h2 style="margin-top:10px">No to-do is active</h2>
            {/each}

        {:else if presentActive.name === "Completed"}
            <h4>{todos.filter(todo => todo.status === "completed").length} out of {todos.length} todos completed.</h4>
            {#each todos.filter(todo => todo.status === "completed") as todo}
                <Todo content={todo.content} 
                    id={todo.key} 
                    edit={todo.edit} 
                    status={todo.status}
                    on:edit={forward} 
                    on:finishEdit={forwardFinishEdit} 
                    on:delete={handleDelete} 
                    on:completed={handleCompleted}
                    on:active={handleActive}
                />
            {:else}
                <h2 style="margin-top:10px">No to-do has been completed</h2>
            {/each}
        {/if}
    </div>
   
</section>

<style>
    h4{
        font-size:24px;
    }
    .todo-container{
        display:flex;
        flex-direction:column;
        gap:10px;
    }
</style>