<script>
    import { Github } from '@lucide/svelte';
    import { page } from '$app/state'
    import { onMount } from 'svelte';
	let { children } = $props();

    let format = $state(null);

    onMount(() => {
        format = Math.floor(Date.now() / (1000)) % 7;
    });
</script>

<header>
    <span></span>
    <a href="/" class:selected={page.url.pathname == "/"}>
        {#if format !== null}
            {#key format}
                {#if format == 1}
                    <h1>Play<sup>2</sup> Game<sup>2</sup></h1>
                {:else if format == 2}
                    <h1>(Play Game)<sup>2</sup></h1>
                {:else if format == 3}
                    <h1>Play Play Game<sup>2</sup></h1>
                {:else if format == 4}
                    <h1>Play<sup>2</sup> Game Game</h1>
                {:else if format == 5}
                    <h1>2Play 2Game</h1>
                {:else if format == 6}
                    <h1>Play<sup>2</sup> × Game<sup>2</sup> = Fun<sup>2</sup></h1>
                {:else}
                    <h1>Play Play Game Game</h1>
                {/if}
            {/key}
        {/if}
    </a>
    <a href="https://github.com/finnbear/playplaygamegame" target="_blank">
        <Github/>
    </a>
</header>
<br/>

{@render children()}

<style>
    h1 {
        margin: 0;
        letter-spacing: .2rem;
        font-size: calc(10px + 3vmin);
    }

    header {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        padding: 0.5rem 0.5rem 0 0.5rem;
    }

    a {
        text-decoration: none;
    }

    a.selected {
        cursor: default;
    }
</style>