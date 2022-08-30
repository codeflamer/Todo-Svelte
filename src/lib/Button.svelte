<script>
    export let name="";
    export let active = true;
    export let del = false;
</script>

<button type="button" class="{!active && "notActive"} {del && "delete"}">
    {name}
</button>

<style>
    button{
        padding:4px 0;
        color:white;
        background: rgb(18, 14, 14);
        cursor: pointer;
        border-radius: 3px;
        flex-grow: 1;
    }
    /* button:hover{
        text-decoration: underline;
    } */
    .notActive{
        background: white;
        color:black;
        border:1px solid #696969;
    }
    .notActive:hover{
        background: rgb(18, 14, 14);
        color:white;
    }
    .delete{
        background:rgb(195, 1, 1);
        color:white;
        border: none;
    }
    .delete:hover{
        background: red;
    }
</style>