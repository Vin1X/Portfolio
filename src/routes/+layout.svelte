<script lang="ts">
	import favicon from "$lib/assets/favicon.svg";
	import { base } from "$app/paths";
	import { page } from "$app/stores";

	let { children } = $props();
	import "../app.css";

	// SEO
	$effect(() => {
		if (typeof document !== "undefined") {
			document.title =
				$page.data?.title || "Vincent Walura | Software Developer";
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

	// Header Scroll Behavior
	let y = $state(0);
	let lastY = $state(0);
	let headerHidden = $state(false);

	$effect(() => {
		const currentY = y;
		const delta = currentY - lastY;

		if (currentY > 50) {
			if (delta > 10) {
				headerHidden = true;
			} else if (delta < -10) {
				headerHidden = false;
			}
		} else {
			headerHidden = false;
		}

		lastY = currentY;
	});

	// Background Blobs
	let blobCount = 3;
	let blobs = $state(
		Array.from({ length: blobCount }).map((_, i) => ({
			id: i,
			size: [
				"w-[26rem] h-[26rem]",
				"w-[30rem] h-[30rem]",
				"w-[22rem] h-[22rem]",
			][i % 3],
			color: ["bg-blue-600/20", "bg-purple-600/15", "bg-cyan-500/15"][
				i % 3
			],
			duration: `${20 + i * 5}s`,
			delay: `${i * -4}s`,
			top: `${15 + ((i * 25) % 50)}%`,
			left: `${15 + ((i * 30) % 50)}%`,
		})),
	);
</script>

<svelte:window bind:scrollY={y} />

<svelte:head>
	<link rel="icon" href={favicon} />
	<meta
		name="robots"
		content="noindex, nofollow, noarchive, nosnippet, noimageindex"
	/>
</svelte:head>

<div class="fixed inset-0 -z-10 overflow-hidden bg-[#030712] text-slate-100">
	<div class="absolute inset-0 opacity-80 pointer-events-none blur-3xl">
		{#each blobs as blob (blob.id)}
			<div
				class="absolute rounded-full {blob.color} {blob.size} animate-float gpu-accelerated"
				style:top={blob.top}
				style:left={blob.left}
				style:animation-duration={blob.duration}
				style:animation-delay={blob.delay}
			></div>
		{/each}
	</div>

	<div
		class="pointer-events-none absolute inset-0 opacity-[0.03] mix-blend-overlay bg-repeat"
		style="background-image: url(&quot;data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noiseFilter'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.8' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noiseFilter)'/%3E%3C/svg%3E&quot;);"
	></div>

	<div
		class="pointer-events-none absolute inset-0 bg-[radial-gradient(ellipse_at_center,transparent_30%,#030712_100%)]"
	></div>
</div>

<div
	class="min-h-screen flex flex-col font-sans selection:bg-cyan-500/30 selection:text-cyan-200"
>
	<header
		class="sticky top-0 z-50 w-full py-4 px-4 sm:px-8 transition-transform duration-300 ease-in-out {headerHidden
			? '-translate-y-full'
			: 'translate-y-0'}"
	>
		<div
			class="max-w-7xl mx-auto flex items-center justify-between relative"
		>
			<div class="w-10 md:w-32 shrink-0"></div>

			<nav
				class="flex items-center gap-1 sm:gap-2 px-3 py-1.5 rounded-full bg-slate-900/70 backdrop-blur-md border border-white/10 shadow-lg text-xs sm:text-sm text-slate-300"
			>
				<a
					href="{base}/"
					class="px-3 py-1.5 rounded-full hover:text-white hover:bg-white/5 transition-all duration-150"
					>Home</a
				>
				<a
					href="{base}/projects"
					class="px-3 py-1.5 rounded-full hover:text-white hover:bg-white/5 transition-all duration-150"
					>Projects</a
				>
			</nav>

			<div class="w-10 md:w-32 flex justify-end shrink-0">
				<a
					href="https://github.com/Vin1X"
					target="_blank"
					rel="noreferrer"
					aria-label="GitHub Profile"
					class="p-2.5 rounded-full text-slate-400 hover:text-white bg-slate-900/60 hover:bg-slate-800 border border-white/10 transition-all duration-200 shadow-sm"
				>
					<svg
						xmlns="http://www.w3.org/2000/svg"
						width="18"
						height="18"
						viewBox="0 0 24 24"
						fill="currentColor"
					>
						<path
							d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.6.113.82-.268.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61-.546-1.387-1.333-1.756-1.333-1.756-1.09-.745.083-.729.083-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.807 1.305 3.492.998.107-.775.418-1.305.762-1.605-2.665-.3-5.466-1.335-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.123-.303-.535-1.523.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.241 2.873.118 3.176.77.84 1.235 1.91 1.235 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.577C20.565 21.795 24 17.3 24 12c0-6.627-5.373-12-12-12z"
						/>
					</svg>
				</a>
			</div>
		</div>
	</header>

	<main class="grow p-4 lg:p-8 max-w-6xl mx-auto w-full animate-fade-in">
		{@render children()}
	</main>

	<footer
		class="py-10 px-6 border-t border-white/5 bg-slate-950/60 backdrop-blur-sm text-slate-400 mt-auto"
	>
		<div class="max-w-6xl mx-auto">
			<div
				class="flex flex-col md:flex-row justify-between items-center gap-6"
			>
				<div class="text-center md:text-left">
					<p class="text-sm">
						© {new Date().getFullYear()} Vincent Walura. All rights
						reserved.
					</p>
				</div>

				<div class="flex items-center gap-6 text-sm">
					<a href="/" class="hover:text-slate-200 transition-colors"
						>Home</a
					>
					<a
						href="/projects"
						class="hover:text-slate-200 transition-colors"
						>Projects</a
					>

					<a
						href="mailto:vincent.walura@hotmail.com"
						aria-label="Send Email"
						class="inline-flex items-center text-slate-400 hover:text-white transition-colors duration-200"
					>
						<svg
							class="w-5 h-5"
							viewBox="0 0 24 24"
							fill="none"
							xmlns="http://www.w3.org/2000/svg"
						>
							<path
								fill-rule="evenodd"
								clip-rule="evenodd"
								d="M3.75 5.25L3 6V18L3.75 18.75H20.25L21 18V6L20.25 5.25H3.75ZM4.5 7.6955V17.25H19.5V7.69525L11.9999 14.5136L4.5 7.6955ZM18.3099 6.75H5.68986L11.9999 12.4864L18.3099 6.75Z"
								fill="currentColor"
							/>
						</svg>
					</a>
				</div>
			</div>
		</div>
	</footer>
</div>

<style>
	.gpu-accelerated {
		will-change: transform;
		transform: translateZ(0);
	}

	@keyframes float {
		0% {
			transform: translate3d(0, 0, 0) scale(1);
		}
		50% {
			transform: translate3d(24px, -18px, 0) scale(1.05);
		}
		100% {
			transform: translate3d(-18px, 24px, 0) scale(0.95);
		}
	}

	.animate-float {
		animation: float 22s infinite ease-in-out alternate;
	}
</style>
