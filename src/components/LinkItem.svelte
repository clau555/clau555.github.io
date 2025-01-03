<script lang="ts">
    import { page } from "$app/stores";
    import { createEventDispatcher } from "svelte";

    const dispatch = createEventDispatcher();

    export let label: string;
    export let link: string;
    export let isHighlighted: boolean = false;
</script>

{#if link === ""}
    <div>
        <span class="disabled">
            {label}
        </span>
        🚧
    </div>
{:else}
    <a
        class:highlighted={isHighlighted}
        href={link}
        aria-current={$page.url.pathname === link}
        on:click={() => dispatch("click")}
    >
        {label}
    </a>
{/if}

<style>
    a {
        color: var(--text-secondary);
        white-space: nowrap;
    }

    a:hover {
        color: var(--text-primary);
        border-color: var(--text-primary);
    }

    .highlighted {
        color: var(--accent);
    }

    .disabled {
        color: var(--text-secondary);
        pointer-events: none;
        text-decoration: line-through;
    }
</style>
