<script>
    import { params } from "@roxi/routify";
    import { onMount } from "svelte";
    export let id;
    let todo;

    onMount(async () => {
        if (id) {
            const res = await fetch(
                `https://jsonplaceholder.typicode.com/todos/${id}`
            );
            if (res.ok) {
                todo = await res.json();
            }
        }
    });
</script>

<h1>TODO Details</h1>
{#if todo && Object.keys(todo)}
    {#each Object.keys(todo) as key}
        <p>{key}: {todo[key]}</p>
    {/each}
{/if}
