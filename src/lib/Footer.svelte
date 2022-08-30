
<script>
import Button from "./Button.svelte";


</script>

<footer>
    <div class="container-footer">
        <Button name="Check All"/>
        <Button name="Remove Completed"/>
    </div>
</footer>

<style>
    .container-footer{
        display:grid;
        grid-template-columns: 1fr 1fr;
        gap:10px;
    }
</style>