<style>
    .player {
        flex-grow: 1;
    }
    .plus {
        background-color: seagreen;
    }
    .minus {
        background-color: brown;
    }
    button {
        font-size: 20px;
        border-radius: 3px;
        width: 40px;
        color: white;
        font-family: monospace;
        font-weight: bold;
    }
    button[disabled] {
        color: grey;
        background-color: lightgrey;
        cursor: not-allowed;
    }
</style>

<script>
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();
    export let score = 0; // letting others know that this is the variable that can be changed
    export let winningText;
    export let won;
    export let fontColor;
    export let gameOver;
    function minus() {
        // dispatch('points', -1);
        score--;
    }

    function plus() {
        score++;
    }


</script>

<div style="color: {fontColor}" class="player">
    <h2>{score}</h2> 
    <button 
        on:click={plus} disabled={gameOver} class="plus">+</button>
    <button 
        on:click={minus} disabled={gameOver} class="minus">-</button>
    {#if won}
        <h2>{winningText}</h2>
    {/if}

</div>
