<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();
    let value = "";
    function handleKeyUp({ key }) {
      if (key !== "Enter" || value.length === 0) return;
      dispatch("newitem", value);
      value = "";
    }
  </script>
  
  <style>
    input {
      box-sizing: border-box;
      margin-bottom: 15px;
      padding: 15px;
      border: none;
      outline: none;
      width: 100%;
      background: rgba(29, 29, 29);
      color: #ffffff;
      font-weight: bold;
      font-size: 1em;
      cursor: pointer;
      border-radius: 10px;
    }
    input,
    input::placeholder {
      color: #ffffff;
    }
  </style>
  
  <input type="text" on:keyup={handleKeyUp} bind:value placeholder="+ Add item" />