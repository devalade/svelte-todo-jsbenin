<script>
   import { fade, scale } from 'svelte/transition'
  export let task;
  export let onDelete;
  export let onComplete;

</script>

<li in:scale out:fade="{{ duration: 500 }}" class="task">
  <div class="task-group">
    <input type="checkbox" name={task.name} checked={task.checked} id={task.id} on:click={() => onComplete(task)} class="checkbox">
    <label for={task.id} class="label">
      {task.name}
      <p class="checkmark">
        <svg xmlns="http://www.w3.org/2000/svg" class="" width="24" height="24" viewBox="0 0 24 24" stroke-width="2" stroke="#FFF" fill="none" stroke-linecap="round" stroke-linejoin="round">
          <path stroke="none" d="M0 0h24v24H0z" fill="none"/>
          <path d="M5 12l5 5l10 -10" />
        </svg>
      </p>
    </label>
  </div>
  <div class="task-group">
    <button class="btn">
      <svg xmlns="http://www.w3.org/2000/svg" class="icon icon-tabler icon-tabler-pencil" width="28" height="28" viewBox="0 0 24 24" stroke-width="2" stroke="#FFF" fill="none" stroke-linecap="round" stroke-linejoin="round">
        <path stroke="none" d="M0 0h24v24H0z" fill="none"/>
        <path d="M4 20h4l10.5 -10.5a1.5 1.5 0 0 0 -4 -4l-10.5 10.5v4" />
        <line x1="13.5" y1="6.5" x2="17.5" y2="10.5" />
      </svg>
    </button>
    <button on:click={() => onDelete(task)} class="btn btn-delete">
     <svg xmlns="http://www.w3.org/2000/svg" class="icon icon-tabler icon-tabler-trash" width="28" height="28" viewBox="0 0 24 24" stroke-width="2" stroke="#FFF" fill="none" stroke-linecap="round" stroke-linejoin="round">
        <path stroke="none" d="M0 0h24v24H0z" fill="none"/>
        <line x1="4" y1="7" x2="20" y2="7" />
        <line x1="10" y1="11" x2="10" y2="17" />
        <line x1="14" y1="11" x2="14" y2="17" />
        <path d="M5 7l1 12a2 2 0 0 0 2 2h8a2 2 0 0 0 2 -2l1 -12" />
        <path d="M9 7v-3a1 1 0 0 1 1 -1h4a1 1 0 0 1 1 1v3" />
      </svg>
    </button>
  </div>
</li>

<style>
  .task {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: .6em;
  font-size: var(--_size);
  border: .2em solid hsl(var(--muted) / 0.8);
  padding: .6em;
  border-radius: calc(var(--_radius) * 2);
}

.task-group {
  display: flex;
  align-items: center;
  --taskgroup-gap: .5em;
  gap: var(--taskgroup-gap);
}

.label {
  position: relative;
  cursor: pointer;
  text-align: left;
  line-height: 1.4;
    background: none;
  transform: none;
  padding: 0;
}

.checkbox {
  flex-shrink: 0;
  appearance: none;
  -webkit-appearance: none;
  border-radius: var(--_radius);
  width: 1em;
  height: 1em;
  background-color: hsl(var(--muted));
  border-radius: var(--_radius);
  box-shadow:
    0 0 .5em hsl(var(--accent) / .1),
    0 0 0 0.05em hsl(var(--accent) / .5),
    0 0 0 -0.2em hsl(var(--accent));
  transition: box-shadow var(--_tspeed_fast) ease-in-out,
    background-color 80ms ease-in-out;
}

.checkbox:focus {
  outline: none;
}

.checkbox:is(:focus-visible, :hover) {
  box-shadow:
    0 0 0 hsl(var(--bg)),
    0 0 0 .05em hsl(var(--accent)),
    0 0 0 .225em hsl(var(--accent) / .3);
}

.checkmark {
  content: '';
  position: absolute;
  width: 1em;
  height: 1em;
  display: grid;
  place-items: center;
  top: 50%;
  color: hsl(var(--muted));
  border-radius: var(--_radius);
  transform: translate3d(calc(-200% - var(--taskgroup-gap)), -60%, 0);
  transition: background-color 80ms ease-in-out;
}

.checkmark svg {
  width: 1.2em;
  height: 1.2em;
}

.checkbox:checked {
  background-color: hsl(var(--accent));
}

.checkbox:checked+label {
  text-decoration: line-through;
}

.btn-delete {
  --accent: var(--accent1);
}

.loading {
  color: hsl(var(--accent));
  font-size: var(--_size);
  font-weight: bold;
  animation: pulse 2s infinite ease-in-out;
}

@keyframes pulse {

  0%,
  100% {
    opacity: 1;
  }

  50% {
    opacity: 0.5;
  }
}

.error {
  color: hsl(var(--accent1));
  font-size: var(--_size);
  text-align: center;
}
</style>