<script lang="ts">
	import {
		Footer,
		FooterCopyright,
		FooterLinkGroup,
		FooterLink,
	} from "flowbite-svelte";
	import HomeOutline from "flowbite-svelte-icons/HomeOutline.svelte";
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

	const colors = [
		"bg-purple-600",
		"bg-blue-500",
		"bg-pink-500",
		"bg-indigo-400",
		"bg-cyan-400",
		"bg-orange-500",
	];

	let blobs = $state(
		Array.from({ length: 12 }).map((_, i) => ({
			id: i,
			size: ["w-32 h-32", "w-32 h-32", "w-48 h-48", "w-64 h-64"][i % 4],
			color: colors[i % colors.length],
			duration: `${20 + i * 5}s`,
			delay: `${i * -3}s`,
			top: `${10 + ((i * 15) % 70)}%`,
			left: `${10 + ((i * 20) % 80)}%`,
		})),
	);
</script>

<div class="fixed inset-0 -z-10 overflow-hidden bg-[#020617]">
	<div class="blob-container h-full w-full opacity-60">
		{#each blobs as blob (blob.id)}
			<div
				class="absolute rounded-full blur-[30px] mix-blend-lighten animate-float {blob.size} {blob.color}"
				style:top={blob.top}
				style:left={blob.left}
				style:animation-duration={blob.duration}
				style:animation-delay={blob.delay}
			></div>
		{/each}
	</div>

	<div class="pointer-events-none absolute inset-0 opacity-[0.03]"></div>

	<div
		class="pointer-events-none absolute inset-0 bg-[radial-gradient(circle_at_center,transparent_0%,rgba(2,6,23,0.6)_100%)]"
	></div>
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
		class=" inline-flex justify-center items-center p-6 bg-transparent text-4xl font-semibold border-2 border-white/40 rounded-4xl gap-14 h-16 my-6 mx-auto lg:min-w-2xl"
	>
		<a
			class="text-[#7dd3fc]! block hover:scale-110 transition-transform duration-300"
			href="{base}/"><HomeOutline class="shrink-0 h-10 w-10" /></a
		>
		<a
			class="text-[#7dd3fc]! block hover:scale-110 transition-transform duration-300"
			href="{base}/projects">Projects</a
		>
	</header>

	<main class="grow p-4 lg:p-8 lg:px-60 animate-fade-in">
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

<svg xmlns="http://www.w3.org/2000/svg" class="hidden">
	<defs>
		<filter id="softGoo">
			<feGaussianBlur
				in="SourceGraphic"
				stdDeviation="35"
				result="blur"
			/>
			<feColorMatrix
				in="blur"
				mode="matrix"
				values="1 0 0 0 0  0 1 0 0 0  0 0 1 0 0  0 0 0 18 -8"
				result="goo"
			/>
			<feComposite in="SourceGraphic" in2="goo" operator="atop" />
		</filter>
	</defs>
</svg>

<style>
	.blob-container {
		filter: url("#softGoo");
		opacity: 0.4;
	}

	@keyframes float {
		0% {
			transform: translate3d(0, 0, 0) scale(1);
		}
		33% {
			transform: translate3d(5vw, -3vh, 0) scale(1.05);
		}
		66% {
			transform: translate3d(-4vw, 4vh, 0) scale(0.95);
		}
		100% {
			transform: translate3d(0, 0, 0) scale(1);
		}
	}

	.animate-float {
		animation: float infinite cubic-bezier(0.45, 0, 0.55, 1) alternate;
	}
</style>
