
<script>
    import { createEventDispatcher } from "svelte";

    import Button from "./Button.svelte";

    const dispatch = createEventDispatcher()

    const handleCheckAll = () =>{
        dispatch("checkall")
    }

    const handleRemoveCompleted = () =>{
        dispatch("removeCompleted")
    }
</script>

<footer>
    <div class="container-footer">
        <Button name="Check All" on:click={handleCheckAll}/>
        <Button name="Remove Completed" on:click={handleRemoveCompleted}/>
    </div>
</footer>

<style>
    .container-footer{
        display:grid;
        grid-template-columns: 1fr 1fr;
        gap:10px;
    }
</style>