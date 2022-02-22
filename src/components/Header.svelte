<script>
    import { items } from "../stores"
    $: itemCount = $items.length;
    $: completedItemCount = $items.filter((item) => item.completed).length;
</script>

<div class="header">
    <div>Svelte To-Do List</div>
    <span>
        {completedItemCount}/{itemCount}
    </span>
</div>

<style>
    .header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 15px 20px;
        color: #eee;
        font-weight: bold;
        font-size: 1.5em;
        background-color: rgb(29, 29, 29);
        border-radius: 10px 10px 0 0;
    }
</style>