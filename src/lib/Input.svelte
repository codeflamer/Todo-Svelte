<script>
import { createEventDispatcher } from "svelte";

    import Button from "./Button.svelte";


    const dispatch = createEventDispatcher()

    let input = "";
    let todo = {
      status:"active",
      content:"",
      edit:false
    }


    const handleAdd = () =>{
        if(input.length === 0){
            return;
        }
        dispatch("add",{
            todo: {...todo,content:input,key:Math.ceil(Math.random() * 1000)}
        })
        input="";
    }
</script>

<section>
    <form on:submit|preventDefault={handleAdd}>
        <input name="task" bind:value={input}/>
        <Button name="Add" on:click={handleAdd}/>
    </form>
</section>

<style>
    form{
        display: flex;
        flex-direction: column;
        width:inherit;
        gap:10px;
    }
    input{
        width:100%;
        outline: none;
        height:40px;
        padding:2px 7px;
    }
    input:focus{
        border:2px dashed black;
    }
    
</style>


