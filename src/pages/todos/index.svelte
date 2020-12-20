<script>
    import { onMount } from "svelte";
    import { todos } from "../example/_data";
    let data = [];
    onMount(async () => {
        const res = await fetch(
            "https://jsonplaceholder.typicode.com/todos/?_limit=10"
        );
        if (res.ok) {
            data = await res.json();
        }
    });
</script>

<style>
    a {
        display: block;
    }
</style>

<h1>Todos</h1>
{#each data as todo}
    <a href="/todos/{todo.id}">{todo.id}. {todo.title}</a>
{/each}
