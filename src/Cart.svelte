<script>
    export let items;

    // $: is a label syntax in JS
    // in Svelte, everything writen after this will be re-executed 
    // whenever any of its input value changes!!! 
    $: cartTotal = items.reduce((sum, curValue) => {
        return sum + curValue.price;
    }, 0);
</script>

<!-- MARKUP ||||||||||||||||||||||||||||| -->
{#if items.length === 0}
    <p>No items in cart, yet!</p>
{:else}
<ul>
    {#each items as item}
        <li>{item.title} - ${item.price}</li>
    {/each}
</ul>

<h1>TOTAL: ${cartTotal}</h1>
{/if}

<style>
    ul {
        list-style: none;
        margin: 1rem;
        padding: 0;
    }

    li {
        margin: .5rem 0;
        padding: .5rem;
        border: 1px solid #aaa;
    }

    h1 {
        font-size: 1.5rem;
        margin: 1rem;
    }
</style>