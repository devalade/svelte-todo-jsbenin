<script>
  import TaskItem from './TaskItem.svelte';


  export let tasks = []; 
  export let onDelete;
  export let onComplete;
  export let onUpdate;

</script>

<div class="tasks">
  {#each tasks  as task (task.id) }
    <TaskItem task={task} onDelete={onDelete} onComplete={onComplete} onUpdate={onUpdate} />
  {/each }
</div>


<style>
  .tasks {
  display: grid;
  list-style-type: none;
  gap: 1.5em;
}
</style>