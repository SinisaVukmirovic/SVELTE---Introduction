<style>
    button {
        font: inherit;
        padding: .25rem .5rem;
        background: royalblue;
        border: 1px solid royalblue;
        color: #fff;
        cursor: pointer;
    }
        button:hover,
        button:active {
            box-shadow: 1px 1px 6px rgba(0, 0, 0, .3);
        }
</style>

<!-- MARKUP |||||||||||||||||||||||||| -->
<button on:click>
    <!-- we have to add an event here for that to simply be "forwarded"
     on to the next parent component, which doesn't have button events -->
    <slot />
    <!-- slot is a standard HTML element and acts as a placeholder -->
</button>