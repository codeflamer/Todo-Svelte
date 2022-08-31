<script>
import Footer from "./lib/Footer.svelte";

import Input from "./lib/Input.svelte";
import Tabs from "./lib/Tabs.svelte";
import Todos from "./lib/Todos.svelte";

  let todos = [
    {
      status:"active",
      key:1,
      content:"Create Svelte App",
      edit:false
    },
    {
      status:"active",
      key:2,
      content:"Finish Svelte App",
      edit:false
    },
    {
      status:"active",
      key:3,
      content:"wake up",
      edit:false
    },
  
  ]

  let stages = [{name:"All",active:true},{name:"Active",active:false},{name:"Completed",active:false}];
  let presentActive={name:"All",active:true};

  const handleEdit = (e) =>{
    console.log("Editting...",e.detail.id);
    const copyArray = [...todos];
    const editedArray = copyArray.map(todo =>{
      if(todo.key === e.detail.id){
        todo.edit=true
      }
      return todo
    })
    todos = editedArray;
  }

  const handleEdited = (e) =>{
    const copyArray = [...todos];
    const editedArray = copyArray.map(todo =>{
      if(todo.key === e.detail.id){
        todo.edit=false
        todo.content = e.detail.content
      }
      return todo
    })
    todos = editedArray;
  }

  const handleDelete = (e) =>{
    const copyArray = [...todos];
    const editedArray = copyArray.filter(todo => todo.key !== e.detail.id);
    todos = editedArray;
  }

  const handleAddTodo = (e) =>{
    console.log("All Clicked",todos)
    const copyArray = [...todos];
    copyArray.push(e.detail.todo);
    todos = copyArray;
  }

  const handleCompleted = (e) =>{
    console.log("completed Clicked",todos)
    const copyArray = [...todos];
    const editedArray = copyArray.map(todo =>{
      if(todo.key === e.detail.id){
        todo.status = "completed"
      }
      return todo;
    })
    todos = editedArray;
    console.log(todos);
  }

  const handleActive = (e) => {
    console.log("Active Clicked",todos)
    const copyArray = [...todos];
    const editedArray = copyArray.map(todo =>{
      if(todo.key === e.detail.id){
        todo.status = "active"
      }
      return todo;
    })
    todos = editedArray;
    console.log(todos);
  }

  const handleSwitch = (e) =>{
    console.log(`${e.detail.name} Clicked: `,todos)
      const copiedStages = [...stages];
      const editedStages = copiedStages.map(stage => {
          stage.active = false;
          if(stage.name === e.detail.name){
              stage.active = true;
              presentActive = stage;
          }
          return stage;
      })
      stages = editedStages;
  }

  const handleCheckAll = (e) =>{
    const copyArray = [...todos];
    const editedArray = copyArray.map(todo =>{
        todo.status = "completed"
        return todo;
    })
    todos = editedArray;
  }

  const handleRemoveCompleted = (e) =>{
    const copyArray = [...todos];
    const editedArray = copyArray.map(todo =>{
        todo.status = "active"
        return todo;
    })
    todos = editedArray;
  }

</script>

<main>
    <h1>What needs to be done?</h1>
    <Input on:add={handleAddTodo}/>
    <div class="content-container">
      <Tabs stages={stages} on:switch={handleSwitch}/>
      <Todos {presentActive} {todos} on:edit={handleEdit} on:finishEdit={handleEdited} on:delete={handleDelete} on:completed={handleCompleted} on:active={handleActive}/>
      <hr/>
      <Footer on:checkall={handleCheckAll} on:removeCompleted={handleRemoveCompleted}/>
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
