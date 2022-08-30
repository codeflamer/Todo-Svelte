
<script>
import { createEventDispatcher } from 'svelte';
import Button from "./Button.svelte";

export let content="";
export let status;
export let id = "";
export let edit;
let editContent = content;

$: check = status==="completed" ? true : false;

let dispatch = createEventDispatcher();

const handleEdit = () => {
    dispatch("edit",{
        id
    })
}

const handleEdited = () =>{
    dispatch("finishEdit",{
        id,
        content:editContent
    })
}

const handleDelete = () => {
    console.log("deleting...");
    dispatch("delete",{
        id
    })
}

const changeState = () =>{
    console.log("clicking on :",content );
    // check = !check;
    const timer = setTimeout(()=>{
        if(check === false){
            dispatch("completed",{
                id
            })
        }
        if(check === true){
            dispatch("active",{
                id
            })
        }

        console.log("status: ",status)
    },500)
    return ()=>clearTimeout(timer);
}

console.log(status)


</script>

<section>
    <div class="todo-content">
        <label class="checkbox-container">
            <!-- checked={status === "completed"? true : false} -->
            
            <input  type="checkbox" checked={status === "completed" ? true : false}/>

            <span class="checkmark" on:click={changeState}></span>
        </label>

        {#if edit}
            <form on:submit|preventDefault={handleEdited}>
                <input type="text" bind:value={editContent} /> 
                
            </form>
        {:else}
            <p >{content}</p>
            <h2>
                {status === "completed" ? "completed" : "active"}
            </h2>
        {/if}
        
    </div>
    <div class="todo-action">
        <Button name="Edit" active={false} on:click={handleEdit}/>
        <Button name="Delete" del={true} on:click={handleDelete}/>
    </div>
</section>

<style>
    section{
        margin-top:15px;
    }
    p{
        font-size:18px;
        margin-top: 6px;
        position:relative;
        top:-5px;
    }
    .todo-content{
        display: flex;
        justify-items: center;
        align-items: center;
        gap:10px;
        height:30px;
        position: relative;
    }

    .todo-content input[type="text"]{
        /* border:0; */
        outline:0;
        font-size:16px;
        padding:3px 8px;
    }

    .todo-action{
        display: flex;
        margin-top:15px;
        justify-content: space-between;
        gap:10px;
    }

    
    .checkbox-container{
        display: block;
        position: relative;
        padding-left: 35px;
        cursor: pointer;
        font-size: 22px;
        -webkit-user-select: none;
        -moz-user-select: none;
        -ms-user-select: none;
        user-select: none;
    }

    .checkbox-container input {
        position: absolute;
        opacity: 1;
        cursor: pointer;
        height: 0px;
        width: 0px;
    }
    .checkmark {
        position: absolute;
        top: -15px;
        left: 0;
        height: 30px;
        width: 30px;
        border:1px solid black;
        
    }
    
    .checkmark:hover{
        cursor: pointer;
    }
   
    .checkmark:after {
        content: "";
        position: absolute;
        display: none;
    }

    .checkbox-container input:checked ~ .checkmark:after {
        display: inline;
        /* background-color:red; */
    }

    .checkmark:after {
        left: 11px;
        top: 5px;
        width: 5px;
        height: 10px;
        border: solid black;
        border-width: 0 3px 3px 0;
        -webkit-transform: rotate(45deg);
        -ms-transform: rotate(45deg);
        transform: rotate(45deg);
    }
</style>