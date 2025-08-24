<script lang="ts">
    import { page } from "$app/stores";
    import { createEventDispatcher } from "svelte";

    const dispatch = createEventDispatcher();

    interface Props {
        label: string;
        link: string;
        isHighlighted?: boolean;
    }
    let { label, link, isHighlighted = false }: Props = $props();
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
        onclick={() => dispatch("click")}
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
