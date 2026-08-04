<script lang="ts">
	import favicon from "$lib/assets/favicon.svg";
	import { HomeOutline, FolderOutline } from "flowbite-svelte-icons";
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
	<div class="absolute inset-0 overflow-hidden pointer-events-none">
		<div class="blob blob-1"></div>
		<div class="blob blob-2"></div>
		<div class="blob blob-3"></div>
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
			class="max-w-7xl mx-auto flex items-center justify-center relative"
		>
			<nav
				class="flex items-center gap-1 sm:gap-2 px-3 py-1.5 rounded-full bg-slate-900/70 backdrop-blur-md border border-white/10 shadow-lg text-xs sm:text-sm text-slate-300"
			>
				<a
					href="{base}/"
					aria-label="Home"
					class="inline-flex items-center gap-2 px-3 py-1.5 rounded-full hover:text-white hover:bg-white/5 transition-all duration-150"
				>
					<HomeOutline class="w-4 h-4 text-cyan-400" />
					<span>Home</span>
				</a>
				<a
					href="{base}/projects"
					aria-label="Projects"
					class="inline-flex items-center gap-2 px-3 py-1.5 rounded-full hover:text-white hover:bg-white/5 transition-all duration-150"
				>
					<FolderOutline class="w-4 h-4 text-cyan-400" />
					<span>Projects</span>
				</a>
			</nav>
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
					<a
						href="{base}/"
						class="hover:text-slate-200 transition-colors">Home</a
					>
					<a
						href="{base}/projects"
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
	@keyframes float {
		0% {
			transform: translate3d(0, 0, 0) scale(1);
		}
		25% {
			transform: translate3d(80px, -50px, 0) scale(1.08);
		}
		50% {
			transform: translate3d(-60px, 60px, 0) scale(0.95);
		}
		75% {
			transform: translate3d(50px, 40px, 0) scale(1.03);
		}
		100% {
			transform: translate3d(0, 0, 0) scale(1);
		}
	}

	.blob {
		position: absolute;
		width: 34rem;
		aspect-ratio: 1;
		border-radius: 9999px;

		background: radial-gradient(
			circle,
			rgb(59 130 246 / 0.25) 0%,
			rgb(59 130 246 / 0.12) 35%,
			transparent 70%
		);

		animation: float 24s ease-in-out infinite;
		will-change: transform;
	}

	.blob-1 {
		top: 10%;
		left: 10%;
	}
	.blob-2 {
		top: 50%;
		left: 55%;
	}
	.blob-3 {
		top: 25%;
		left: 70%;
	}
</style>
