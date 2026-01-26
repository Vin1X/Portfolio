<script lang="ts">
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
	import "../app.css";

	// Background
	import {onMount} from 'svelte';
	interface Star {
		x: number;
		y: number;
		size: number;
		opacity: number;
    }

	let stars_slow = $state<Star[]>([]);
	let stars_medium = $state<Star[]>([]);
	let stars_fast = $state<Star[]>([]);
	const COUNT = 60;

	onMount(() => {
		stars_slow = Array.from({ length: COUNT }).map(() => ({
			x: Math.random() * 100,
			y: Math.random() * 100,
			size: Math.random() * 2 + 1,
			opacity: Math.random()
		}));
		stars_medium = Array.from({ length: COUNT }).map(() => ({
			x: Math.random() * 100,
			y: Math.random() * 100,
			size: Math.random() * 2 + 1,
			opacity: Math.random()
		}));
		stars_fast = Array.from({ length: COUNT }).map(() => ({
			x: Math.random() * 100,
			y: Math.random() * 100,
			size: Math.random() * 2 + 1,
			opacity: Math.random()
		}));
	});
</script>

<div class="space pointer-events-none">
	<div class="star-layer slow">
		{#each stars_slow as star}
			<div
			class="star"
			style:left="{star.x}%"
			style:top="{star.y}%"
			style:width="{star.size}px"
			style:height="{star.size}px"
			style:opacity="{star.opacity}"
			></div>
		{/each}
	</div>
	<div class="star-layer medium">
		{#each stars_medium as star}
			<div
			class="star"
			style:left="{star.x}%"
			style:top="{star.y}%"
			style:width="{star.size}px"
			style:height="{star.size}px"
			style:opacity="{star.opacity}"
			></div>
		{/each}
	</div>
	<div class="star-layer fast">
		{#each stars_fast as star}
			<div
			class="star"
			style:left="{star.x}%"
			style:top="{star.y}%"
			style:width="{star.size}px"
			style:height="{star.size}px"
			style:opacity="{star.opacity}"
			></div>
		{/each}
	</div>
</div>

<style>
@keyframes star-slow {
	from { transform: translate3d(0, 0, 0) rotate(0.2deg); opacity: 0.4;}
	to { transform: translate3d(-10px, -5px, 0) rotate(-0.2deg); opacity: 1;}
}


@keyframes star-medium {
	from { transform: translate3d(0, 0, 0) rotate(0.2deg); opacity: 0.4;}
	to { transform: translate3d(-20px, -10px, 0) rotate(-0.2deg); opacity: 1;}
}


@keyframes star-fast {
	from { transform: translate3d(0, 0, 0) rotate(0.2deg); opacity: 0.4;}
	to { transform: translate3d(-30px, -15px, 0) rotate(-0.2deg); opacity: 1;}
}

.space {
    position: fixed;
    inset: 0;
    background: #0a0b1e;
    z-index: -1;
    overflow: hidden;
}

.star-layer {
	position: absolute;
	inset: 0;
	will-change: transform;
}

.star-layer.slow {
	animation: star-slow 30s linear infinite alternate;
}

.star-layer.medium {
	animation: star-medium 15s linear infinite alternate;
}

.star-layer.fast {
	animation: star-fast 10s linear infinite alternate;
}

.star {
	position: absolute;
	background: white;
	border-radius: 50%;
}

</style>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<!-- Scale Head<->Content<->Foot correctly -->
<div class="min-h-screen flex flex-col">
	<header class="text-center p-4 bg-gray-800 text-white text-5xl font-semibold border-b border-gray-700">
		Header
	</header>

	<main class="grow px-4 md:px-8 lg:px-16">
		{@render children()}
	</main>

	<footer class="text-center p-4 text-sm text-gray-500">
		Footer
	</footer>
</div>