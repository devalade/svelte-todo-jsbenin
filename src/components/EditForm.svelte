<script>
    export let task;
    export let onUpdate;
    export let hideEditForm;

    let text = task.name;
    let btnDisabled = true;

    

    const handleSubmit = () => {
        onUpdate(task, text)
        console.log({text})
        hideEditForm();
        text = '';
    }

</script>
    <form class="todo" on:submit|preventDefault={handleSubmit}>

        <div class="wrapper">
            <input type="text" 
                id="task" 
                class="input" 
                placeholder="Renseigner une tâche"
                required 
                autofocus 
                maxlength={60}
                bind:value={text}
            >
            <label for="task" class="label">Modifier une tâche</label>
        </div>
        <button class="btn" aria-label="Add Task" type="submit">
            <svg xmlns="http://www.w3.org/2000/svg" class="icon icon-tabler icon-tabler-device-floppy" width="28" height="28" viewBox="0 0 24 24" stroke-width="1.5" stroke="#FFF" fill="none" stroke-linecap="round" stroke-linejoin="round">
  <path stroke="none" d="M0 0h24v24H0z" fill="none"/>
  <path d="M6 4h10l4 4v10a2 2 0 0 1 -2 2h-12a2 2 0 0 1 -2 -2v-12a2 2 0 0 1 2 -2" />
  <circle cx="12" cy="14" r="2" />
  <polyline points="14 4 14 8 8 8 8 4" />
</svg>
        </button>
    </form>

    <style>
        .todo {
            padding: 0 1rem;
        }
    </style>