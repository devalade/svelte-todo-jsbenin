<script>
    import {createEventDispatcher} from 'svelte';

    let task = '';
    let btnDisabled = true;

    const dispatch = createEventDispatcher();

     const handleInput = () => {
        if(task.trim().length < 1) {
            btnDisabled = true
        } else {
            btnDisabled = false
        }
    }

    const handleSubmit = () => {
        dispatch('add-task', task);
        task = '';
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
                on:input="{handleInput}"
                bind:value="{task}"
            >
            <label for="task" class="label">Renseigner une tâche</label>
        </div>
        <button class="btn" aria-label="Add Task" type="submit">
            <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" stroke-width="1.5" stroke="#FFF" fill="none" stroke-linecap="round" stroke-linejoin="round">
                <path stroke="none" d="M0 0h24v24H0z" fill="none"/>
                <line x1="12" y1="5" x2="12" y2="19" />
                <line x1="5" y1="12" x2="19" y2="12" />
            </svg>
        </button>
    </form>
