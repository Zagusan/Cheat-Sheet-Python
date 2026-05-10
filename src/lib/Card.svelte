<script lang="ts">
    let {
        children = undefined,
        fillParent = false,
        revealId = ""
    } = $props();
</script>

<div class:fill-parent={fillParent} class="card-root">
    {@render children?.()}
    <div class="card-bg" data-id={revealId}></div>
</div>

<style>
    :global(.card-root)
    {
        display: grid;
        grid-template-rows: 100%;
    }

    :global(.card-root>*)
    {
        grid-area: 1/1;
        margin: auto;
    }

    .card-bg
    {
        width: 100%;
        height: 100%;
        border-radius: 16px;
        background-color: var(--card-color);
    }

    .fill-parent
    {
        width: 100%;
        height: 100%;
    }
</style>