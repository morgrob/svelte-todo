<script>
    import { createEventDispatcher } from "svelte";

    export let id, text, completed;

    const dispatch = createEventDispatcher();

    function triggerUpdate() {
        dispatch("update", { id, text, completed });
    }
    function handleDoubleClick() {
        const yes = confirm("Are you sure you wish to delete this item?");
        if (yes) {
            dispatch("delete", id);
        }
    }
</script>

<div class="item" class:completed on:dblclick={handleDoubleClick}>
    <input
      class="text-input"
      type="text"
      bind:value={text}
      readonly={completed}
      on:keyup={({ key, target }) => key === 'Enter' && target.blur()}
      on:blur={() => triggerUpdate()} />
    <input
      class="complete-checkbox"
      type="checkbox"
      bind:checked={completed}
      on:change={() => triggerUpdate()} />
  </div>

<style>
    .item {
    display: flex;
    align-items: center;
    padding: 15px;
    margin-bottom: 10px;
    background: rgb(0, 107, 194);
    border-radius: 10px;
  }
  .item:focus-within {
    background: rgb(39, 39, 39);
  }
  .item.completed {
    background: rgb(29, 29, 29);
  }
  .item.completed .text-input {
    color: white;
    text-decoration: line-through;
  }
  .text-input {
    flex-grow: 1;
    background: none;
    border: none;
    outline: none;
    font-weight: 500;
    font-size: 1em;
    color: white;
  }
  .complete-checkbox {
    margin-left: 15px;
  }
</style>