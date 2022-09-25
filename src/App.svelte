<script>
  import CustomForm from './components/CustomForm.svelte';

  const addTask = (task) => {
    console.log(task.detail);
  }

</script>

<main class="container">
  <header>
    <h1>Mes tâches</h1>
  </header>
  <CustomForm on:add-task={addTask} />

</main>

