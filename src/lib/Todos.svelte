<script>
    import Todo from "./Todo.svelte";

</script>

<section>
   <h4>2 out of 3 items completed.</h4>
   <div class="todo-container">
        <Todo content="Create Svelte App"/>
        <Todo content="Create your first component"/>
        <Todo content = "Create the rest of the tutorial"/>
        <Todo content="Resume Your Escrow shit"/>
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