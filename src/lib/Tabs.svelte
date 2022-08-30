<script>
    import ButtonTabs from "./ButtonTabs.svelte";
    import { createEventDispatcher } from "svelte";

    export let stages = [];

    let dispatch = createEventDispatcher()

    const handleSwitch = (e) =>{
        dispatch("switch",{
            name:e.detail.name
        })
    }
</script>

<section>
    <div class="tab-container">
        {#each stages as stage}
            <ButtonTabs name={stage.name} active={stage.active} on:switch={handleSwitch}/>
        {/each}
    </div>
</section>

<style>
    .tab-container{
        display:grid;
        grid-template-columns: 1fr 1fr 1fr;
        gap:10px;
    }
</style>