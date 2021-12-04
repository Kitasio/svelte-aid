<script lang="ts">
	export let src: string;
	export let srcMobile: string = src;
	export let alt: string = "";
	export let classes: string = "";
	export let loading: string = "lazy";

	import { browser } from "$app/env";
	import { onMount } from "svelte";

	let loaded: boolean = false;
	let thisImage: any;
	let w: number = 600;

	const handleError = () => {
		thisImage.style.display = "none";
	};

	onMount(() => {
		thisImage.onload = () => {
			loaded = true;
		};
	});
</script>

<svelte:window bind:innerWidth={w}/>

{#if w < 600}
	<img
		src={srcMobile}
		{alt}
		{loading}
		class={classes}
		class:loaded
		bind:this={thisImage}
		on:error={handleError}
	/>
{:else if w >= 600}
	<img
		{src}
		{alt}
		{loading}
		class={classes}
		class:loaded
		bind:this={thisImage}
		on:error={handleError}
	/>
{/if}

<style>
	img {
		opacity: 0;
		transition: opacity 500ms ease-out;
	}
	img.loaded {
		opacity: 1;
	}
</style>
