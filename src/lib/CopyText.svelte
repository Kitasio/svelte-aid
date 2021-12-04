<script lang="ts">
    import { fly } from "svelte/transition";

    export let text: string;
    export let useText: boolean = false;
    export let onCopyText: string = "Copied!";
    export let colorActive: string = "blue";
    export let color: string = "black";

    let showCopied = false;
    function copy() {
        navigator.clipboard.writeText(text);
        showCopied = true;
        setTimeout(() => {
            showCopied = false;
        }, 500);
    }
</script>

<div
    class="flex space-x-2"
    style="--theme-color: {color}; --theme-color-hover: {colorActive}"
>
    {#if !showCopied && !useText}
        <svg
            in:fly={{ y: 10, duration: 200 }}
            class="color color-hover stroke-current stroke-2 transition duration-300 hover:rotate-6 w-6 h-6 cursor-pointer"
            on:click|stopPropagation={copy}
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
        >
            <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M8 7v8a2 2 0 002 2h6M8 7V5a2 2 0 012-2h4.586a1 1 0 01.707.293l4.414 4.414a1 1 0 01.293.707V15a2 2 0 01-2 2h-2M8 7H6a2 2 0 00-2 2v10a2 2 0 002 2h8a2 2 0 002-2v-2"
            />
        </svg>
    {:else if useText}
        <svg
            class="color color-hover stroke-current stroke-2 transition duration-300 hover:rotate-6 w-6 h-6 cursor-pointer"
            on:click|stopPropagation={copy}
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
        >
            <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M8 7v8a2 2 0 002 2h6M8 7V5a2 2 0 012-2h4.586a1 1 0 01.707.293l4.414 4.414a1 1 0 01.293.707V15a2 2 0 01-2 2h-2M8 7H6a2 2 0 00-2 2v10a2 2 0 002 2h8a2 2 0 002-2v-2"
            />
        </svg>
    {/if}

    {#if showCopied && useText}
        <p
            style="--theme-copy-color: {colorActive}"
            in:fly={{ y: 10, duration: 200 }}
            out:fly={{ y: -10, duration: 200 }}
            class="text-xs copy-text-color"
        >
            {onCopyText}
        </p>
    {:else if showCopied && !useText}
        <svg
            in:fly={{ y: 10, duration: 200 }}
            style="--theme-copy-color: {colorActive}"
            xmlns="http://www.w3.org/2000/svg"
            class="h-6 w-6 stroke-current stroke-2 copy-text-color"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
        >
            <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M5 13l4 4L19 7"
            />
        </svg>
    {/if}
</div>

<style>
    .color {
        --tw-text-opacity: 1;
        color: var(--theme-color);
    }
    .color-hover:hover {
        --tw-text-opacity: 1;
        color: var(--theme-color-hover);
    }
    .copy-text-color {
        --tw-text-opacity: 1;
        color: var(--theme-copy-color);
    }
</style>
