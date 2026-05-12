<script lang="ts">
    let {
        children = undefined,
        alignItems = "center",
        justifyContent = "center",
        padding = "",
        gap = ""
    } = $props();
</script>

<div class="column" style="gap: {gap}; --padding: {padding}; justify-content: {justifyContent}; align-items: {alignItems}">
    {@render children?.()}
</div>

<style>
    .column
    {
        width: 100%;
        height: 100%;
        display: flex;
        flex-direction: column;
        box-sizing: border-box;
        z-index: 1;
        padding: var(--padding);
    }

    @media (max-width: 850px) 
    {
        .column
        {
            padding: calc(var(--padding) / 2);
        }
    }
</style>