<script>
import Button from "./Button.svelte";

</script>

<section>
    <div class="tab-container">
        <Button name="All" active={true}/>
        <Button name="Active" active={false}/>
        <Button name="Completed" active={false}/>
    </div>
</section>

<style>
    .tab-container{
        display:grid;
        grid-template-columns: 1fr 1fr 1fr;
        gap:10px;
    }
</style>