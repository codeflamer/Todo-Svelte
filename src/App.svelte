<script>
import Footer from "./lib/Footer.svelte";

import Input from "./lib/Input.svelte";
import Tabs from "./lib/Tabs.svelte";
import Todos from "./lib/Todos.svelte";


</script>

<main>
    <h1>What needs to be done?</h1>
    <Input/>
    <div class="content-container">
      <Tabs/>
      <Todos/>
      <hr/>
      <Footer/>
    </div>
    
</main>

<style>
  h1{
    text-align: center;
  }
    main{
      /* border:1px solid gray; */
      max-width: 800px;
      margin:50px auto;
      display:flex;
      flex-direction:column;
      padding:30px 20px;
      gap:20px;
      border-radius: 2px;
      background: white;
      box-shadow: 4px 3px 5px #C8C8C8;
    }
    .content-container{
      display:flex;
      flex-direction:column;
      width:85%;
      margin:0 auto;
      gap:20px;
    }
</style>
