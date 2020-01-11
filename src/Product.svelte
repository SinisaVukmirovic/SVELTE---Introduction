<script>
    import { createEventDispatcher } from 'svelte';

    import Button from './Button.svelte';

    // avoiding to use same names to avoid confusion but same names can be used!
    export let productTitle; 
    export let productPrice;
    export let productDescription;
    // these variables are props and if exported with export keyword means that they
    // can be set from putside of this component

    const dispatch = createEventDispatcher();

    function addToCart() {
        dispatch('addcart', productTitle);
    }
</script>

<style>
    div {
        margin: 1rem;
        box-shadow: 0 2px 8px rgba(0, 0, 0, .3);
        padding: 1rem;
        border-radius: 8px;
        background-color: #fff;
    }

    h1 {
        font-size: 1.25rem;
        margin: .25rem 0;
    }

    h2 {
        font-size: 1rem;
        margin: .25rem 0;
        color: #777;
    }

    p {
        margin: .25rem 0;
    }
</style>

<div>
    <h1>{productTitle}</h1>
    <h2>{productPrice}</h2>
    <p>{productDescription}</p>

    <Button on:click={addToCart}>Add to Cart</Button>
</div>