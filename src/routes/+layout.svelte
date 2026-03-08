<script lang="ts">
	import {
		Footer,
		FooterCopyright,
		FooterLinkGroup,
		FooterLink,
	} from "flowbite-svelte";
	import favicon from "$lib/assets/favicon.svg";
	import { base } from "$app/paths";
	import { page } from "$app/stores";

	let { children } = $props();
	import "../app.css";

	// SEO - Set page title and description
	$effect(() => {
		if (typeof document !== "undefined") {
			document.title = $page.data?.title || "Portfolio";
			const metaDescription = document.querySelector(
				'meta[name="description"]',
			);
			if (metaDescription) {
				metaDescription.setAttribute(
					"content",
					$page.data?.description || "Portfolio",
				);
			}
		}
	});

	// Background
	import { onMount } from "svelte";
	interface Star {
		x: number;
		y: number;
		size: number;
		opacity: number;
	}

	let stars_slow = $state<Star[]>([]);
	let stars_medium = $state<Star[]>([]);
	let stars_fast = $state<Star[]>([]);
	const COUNT = 100;

	onMount(() => {
		stars_slow = Array.from({ length: COUNT }).map(() => ({
			x: Math.random() * 100,
			y: Math.random() * 100,
			size: Math.random() * 3 + 1,
			opacity: Math.random(),
		}));
		stars_medium = Array.from({ length: COUNT }).map(() => ({
			x: Math.random() * 100,
			y: Math.random() * 100,
			size: Math.random() * 3 + 1,
			opacity: Math.random(),
		}));
		stars_fast = Array.from({ length: COUNT }).map(() => ({
			x: Math.random() * 100,
			y: Math.random() * 100,
			size: Math.random() * 3 + 1,
			opacity: Math.random(),
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
				style:opacity={star.opacity}
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
				style:opacity={star.opacity}
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
				style:opacity={star.opacity}
			></div>
		{/each}
	</div>
</div>

<svelte:head>
	<link rel="icon" href={favicon} />
	<meta
		name="robots"
		content="noindex, nofollow, noarchive, nosnippet, noimageindex"
	/>
</svelte:head>

<!-- Scale Head<->Content<->Foot correctly -->
<div class="min-h-screen flex flex-col">
	<header
		class="flex justify-start items-center w-full p-4 bg-gray-800/80 text-white text-3xl font-semibold border-b border-gray-700 gap-8 h-16"
	>
		<a
			class="block hover:scale-110 transition-transform duration-300"
			href="{base}/">Home</a
		>
		<a
			class="block hover:scale-110 transition-transform duration-300"
			href="{base}/projects">Projects</a
		>
	</header>

	<main class="grow p-4 md:px-8 lg:px-48 animate-fade-in">
		{@render children()}
	</main>

	<Footer class="bg-transparent">
		<FooterCopyright by="Vincent Walura." year={2026} />
		<FooterLinkGroup
			class="mt-3 flex flex-wrap items-center text-sm sm:mt-0 text-gray-500 dark:text-gray-400"
		>
			<FooterLink href="{base}/">Home</FooterLink>
			<FooterLink href="{base}/projects">Projects</FooterLink>
		</FooterLinkGroup>
	</Footer>
</div>

<style>
	@keyframes star-slow {
		from {
			transform: translate3d(0, 0, 0) rotate(1deg);
			opacity: 0.4;
		}
		to {
			transform: translate3d(-10px, -5px, 0) rotate(-1deg);
			opacity: 1;
		}
	}

	@keyframes star-medium {
		from {
			transform: translate3d(0, 0, 0) rotate(1deg);
			opacity: 0.4;
		}
		to {
			transform: translate3d(-20px, -10px, 0) rotate(-1deg);
			opacity: 1;
		}
	}

	@keyframes star-fast {
		from {
			transform: translate3d(0, 0, 0) rotate(1deg);
			opacity: 0.4;
		}
		to {
			transform: translate3d(-30px, -15px, 0) rotate(-1deg);
			opacity: 1;
		}
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
		animation: star-slow 20s linear infinite alternate;
	}

	.star-layer.medium {
		animation: star-medium 10s linear infinite alternate;
	}

	.star-layer.fast {
		animation: star-fast 6s linear infinite alternate;
	}

	.star {
		position: absolute;
		background: white;
		border-radius: 50%;
	}
</style>
