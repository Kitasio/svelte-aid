<script lang="ts">
	export let src: string;
	export let alt: string;
    export let classes: string;

	import { onMount } from 'svelte';

	let loaded: boolean = false;
	let thisImage: any;

	const handleError = () => {
		thisImage.style.display='none'
	}

	onMount(() => {
		thisImage.onload = () => {
			loaded = true;
		};
	});
</script>

<img {src} {alt} class:loaded class={classes} bind:this={thisImage} on:error={handleError} />

<style>
	img {
		opacity: 0;
		transition: opacity 500ms ease-out;
	}
	img.loaded {
		opacity: 1;
	}
</style>
