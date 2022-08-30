
<script>
import Button from "./Button.svelte";

export let content=""

</script>

<section>
    <div class="todo-content">
        <label class="checkbox-container">
            <p>{content}</p>
            <input type="checkbox" checked/>
            <span class="checkmark"></span>
        </label>
        
    </div>
    <div class="todo-action">
        <Button name="Edit" active={false}/>
        <Button name="Delete" del={true}/>
    </div>
</section>

<style>
    section{
        margin-top:15px;
    }
    p{
        font-size:16px;
        margin-top: 6px;
    }
    .todo-content{
        display: flex;
        justify-items: center;
        align-items: center;
        gap:10px;
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
        width: 0;
    }
    .checkmark {
        position: absolute;
        top: 0;
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
        display: block;
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