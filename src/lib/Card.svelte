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
        min-height: 100%;
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
        border: 1px solid var(--card-border);
        border-radius: 14px;
        background:
            linear-gradient(180deg, var(--card-color-start), transparent 44%),
            var(--card-color-end);
        box-shadow: var(--shadow);
        transition:
            border-color 160ms ease,
            box-shadow 160ms ease,
            transform 160ms ease;
    }

    :global(.card-root:hover) .card-bg
    {
        border-color: color-mix(in srgb, var(--accent-cyan), var(--card-border) 58%);
        box-shadow: var(--shadow), 0 0 0 4px rgb(21 154 163 / 0.08);
        transform: translateY(-2px);
    }

    .fill-parent
    {
        width: 100%;
        height: 100%;
    }
</style>
