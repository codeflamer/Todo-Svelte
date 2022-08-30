<script>
import Button from "./Button.svelte"

    const handleSubmit = () =>{
        console.log("submitting..")
    }
</script>

<section>
    <form on:submit|preventDefault={handleSubmit}>
        <input name="task" />
        <Button name="Add"/>
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


