<script>
  import CustomForm from './components/CustomForm.svelte';
  import EditForm from './components/EditForm.svelte';
  import TaskList from './components/TaskList.svelte';
  let tasks = [];


  const addTask = (task) => {
    console.log(task.detail);
    tasks = [task.detail, ...tasks];
  }

  const onDelete = (task) => {
    console.log({tasks})
    tasks = tasks.filter((value) => value.id != task.id);
  }
  
 const onComplete = (task) => {
    tasks = tasks.map((value ) => value.id == task.id ? {...value, completed: !value.completed} : value );
    console.log(tasks)
  }
  const onUpdate = (task, text) => {
    tasks = tasks.map((value ) => value.id == task.id ? {...value, name: text} : value );
  }

</script>

<main class="container">
  <header>
    <h1>Mes tâches</h1>
  </header>
  <CustomForm on:add-task={addTask} />
  {#if tasks.length > 0}
    <TaskList tasks={tasks} onDelete={onDelete} onComplete={onComplete} onUpdate={onUpdate} />
  {/if}
</main>

