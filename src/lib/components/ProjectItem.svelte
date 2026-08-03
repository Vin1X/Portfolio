<script lang="ts">
    import {
        ChevronDoubleUpOutline,
        ChevronDoubleDownOutline,
        CaretRightOutline,
        CaretLeftOutline,
        ExpandOutline,
        CloseOutline,
    } from "flowbite-svelte-icons";
    import type { Component } from "svelte";
    import type { HTMLImgAttributes } from "svelte/elements";

    export interface ImageItem extends HTMLImgAttributes {
        alt?: string;
        src?: string;
        title?: string;
    }

    interface ActionItem {
        label: string;
        text: string;
    }

    interface Project {
        id: string;
        title: string;
        category: string;
        situation: string;
        task: string;
        result: string;
        actions: ActionItem[];
        images: ImageItem[];
    }

    let { project }: { project: Project } = $props();

    let activeImageIndex = $state(0);
    let isOpen = $state(false);
    let isMaximized = $state(false); // Modal state

    let activeImage = $derived(
        project.images[activeImageIndex] ?? project.images[0],
    );

    function nextImage(e?: MouseEvent) {
        if (e) e.stopPropagation();
        if (!project.images.length) return;
        activeImageIndex = (activeImageIndex + 1) % project.images.length;
    }

    function prevImage(e?: MouseEvent) {
        if (e) e.stopPropagation();
        if (!project.images.length) return;
        activeImageIndex =
            (activeImageIndex - 1 + project.images.length) %
            project.images.length;
    }

    function handleKeydown(e: KeyboardEvent) {
        if (!isMaximized) return;
        if (e.key === "Escape") isMaximized = false;
        if (e.key === "ArrowRight") nextImage();
        if (e.key === "ArrowLeft") prevImage();
    }
</script>

<!-- Global keydown listener when lightbox is open -->
<svelte:window onkeydown={handleKeydown} />

<div
    class="bg-slate-900/60 backdrop-blur-xl border border-white/10 rounded-3xl shadow-xl overflow-hidden"
>
    <!-- Accordion Header -->
    <button
        type="button"
        onclick={() => (isOpen = !isOpen)}
        class="w-full p-6 text-left flex justify-between items-center cursor-pointer hover:bg-white/5 transition-colors"
    >
        <div class="flex flex-col">
            <span
                class="text-xs font-mono uppercase tracking-wider text-cyan-400 font-semibold mb-1"
            >
                {project.category}
            </span>
            <span
                class="text-xl sm:text-2xl font-bold text-white hover:text-cyan-300 transition-colors"
            >
                {project.title}
            </span>
        </div>
        <div>
            {#if isOpen}
                <ChevronDoubleUpOutline class="h-5 w-5 text-cyan-400" />
            {:else}
                <ChevronDoubleDownOutline class="h-5 w-5 text-slate-400" />
            {/if}
        </div>
    </button>

    <!-- Collapsible Body -->
    {#if isOpen}
        <div class="p-6 pt-0 border-t border-white/5">
            <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 my-4">
                <!-- Text Content -->
                <div
                    class="lg:col-span-7 space-y-4 text-slate-300 text-base leading-relaxed"
                >
                    <div>
                        <h4
                            class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                        >
                            Situation
                        </h4>
                        <p>{project.situation}</p>
                    </div>

                    <div>
                        <h4
                            class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                        >
                            Task
                        </h4>
                        <p>{project.task}</p>
                    </div>

                    <div>
                        <h4
                            class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                        >
                            Action
                        </h4>
                        <ul
                            class="list-disc list-inside space-y-1 ml-1 text-slate-300"
                        >
                            {#each project.actions as action}
                                <li>
                                    <strong class="text-slate-100"
                                        >{action.label}:</strong
                                    >
                                    {action.text}
                                </li>
                            {/each}
                        </ul>
                    </div>

                    <div>
                        <h4
                            class="font-semibold text-cyan-300 uppercase text-xs tracking-wider font-mono mb-1"
                        >
                            Result
                        </h4>
                        <p>{project.result}</p>
                    </div>
                </div>

                <!-- Image Gallery Container -->
                <div class="lg:col-span-5 flex flex-col justify-start">
                    <div
                        class="group relative w-full h-90 rounded-2xl bg-slate-950/80 border border-white/10 p-2 shadow-inner overflow-hidden flex items-center justify-center"
                    >
                        {#if activeImage?.src}
                            <button
                                type="button"
                                onclick={() => (isMaximized = true)}
                                class="cursor-zoom-in border-0 bg-transparent p-0 flex items-center justify-center focus:outline-none focus:ring-2 focus:ring-cyan-400 rounded-lg"
                                aria-label={`Open enlarged view of ${activeImage.alt ?? project.title}`}
                            >
                                <img
                                    src={activeImage.src}
                                    alt={activeImage.alt ?? project.title}
                                    class="object-contain max-h-85 w-auto mx-auto rounded-lg"
                                    loading={activeImageIndex === 0
                                        ? "eager"
                                        : "lazy"}
                                    decoding="async"
                                />
                            </button>

                            <!-- Maximize Button (Top Right) -->
                            <button
                                type="button"
                                onclick={() => (isMaximized = true)}
                                aria-label="Maximize image view"
                                class="absolute top-3 right-3 z-10 p-2 rounded-xl bg-slate-900/80 text-cyan-300 hover:bg-cyan-500 hover:text-slate-950 transition-all border border-cyan-500/30 backdrop-blur-md opacity-80 group-hover:opacity-100"
                            >
                                <ExpandOutline class="w-4 h-4" />
                            </button>

                            {#if project.images.length > 1}
                                <!-- Left/Right Navigation -->
                                <button
                                    type="button"
                                    onclick={prevImage}
                                    aria-label="Previous image"
                                    class="absolute left-3 top-1/2 -translate-y-1/2 z-10 p-2 rounded-full bg-slate-900/80 text-cyan-300 hover:bg-cyan-500 hover:text-slate-950 transition-colors border border-cyan-500/30 backdrop-blur-md"
                                >
                                    <CaretLeftOutline class="w-4 h-4" />
                                </button>
                                <button
                                    type="button"
                                    onclick={nextImage}
                                    aria-label="Next image"
                                    class="absolute right-3 top-1/2 -translate-y-1/2 z-10 p-2 rounded-full bg-slate-900/80 text-cyan-300 hover:bg-cyan-500 hover:text-slate-950 transition-colors border border-cyan-500/30 backdrop-blur-md"
                                >
                                    <CaretRightOutline class="w-4 h-4" />
                                </button>

                                <!-- Indicators -->
                                <div
                                    class="absolute bottom-3 left-1/2 -translate-x-1/2 z-10 flex gap-1.5"
                                >
                                    {#each project.images as _, i}
                                        <button
                                            type="button"
                                            onclick={(e) => {
                                                e.stopPropagation();
                                                activeImageIndex = i;
                                            }}
                                            aria-label={`Go to image ${i + 1} of ${project.images.length}`}
                                            aria-current={i === activeImageIndex
                                                ? "true"
                                                : undefined}
                                            class="h-2 rounded-full transition-all duration-300 {i ===
                                            activeImageIndex
                                                ? 'w-5 bg-cyan-400'
                                                : 'w-2 bg-slate-600 hover:bg-slate-400'}"
                                        ></button>
                                    {/each}
                                </div>
                            {/if}
                        {/if}
                    </div>

                    <p
                        class="mt-3 text-xs text-center text-slate-400 font-mono italic bg-slate-950/40 p-2 rounded-xl border border-white/5"
                    >
                        {activeImage?.alt ?? ""}
                    </p>
                </div>
            </div>
        </div>
    {/if}
</div>

<!-- Fullscreen Lightbox Modal -->
{#if isMaximized && activeImage?.src}
    <div
        class="fixed inset-0 z-50 min-h-screen w-screen flex items-center justify-center bg-slate-950/90 backdrop-blur-md p-4 sm:p-8 overflow-y-auto"
        role="dialog"
        aria-modal="true"
        aria-label="Expanded image viewer"
    >
        <!-- Click backdrop to close -->
        <button
            type="button"
            class="absolute inset-0 w-full h-full cursor-default"
            onclick={() => (isMaximized = false)}
            aria-label="Close full view"
        ></button>

        <div
            class="relative z-10 max-w-6xl max-h-[90vh] flex flex-col items-center"
        >
            <!-- Close Button -->
            <button
                type="button"
                onclick={() => (isMaximized = false)}
                aria-label="Close expanded view"
                class="absolute -top-12 right-0 p-2 rounded-full bg-slate-900 text-cyan-400 hover:bg-cyan-500 hover:text-slate-950 transition-colors border border-cyan-500/30"
            >
                <CloseOutline class="w-6 h-6" />
            </button>

            <!-- Full-size Image -->
            <img
                src={activeImage.src}
                alt={activeImage.alt ?? project.title}
                class="max-h-[80vh] max-w-full object-contain rounded-xl shadow-2xl border border-white/10"
            />

            <!-- Modal Nav Buttons (If multiple images) -->
            {#if project.images.length > 1}
                <button
                    type="button"
                    onclick={prevImage}
                    aria-label="Previous image"
                    class="absolute left-2 sm:-left-12 top-1/2 -translate-y-1/2 p-3 rounded-full bg-slate-900/90 text-cyan-300 hover:bg-cyan-500 hover:text-slate-950 transition-colors border border-cyan-500/30"
                >
                    <CaretLeftOutline class="w-6 h-6" />
                </button>
                <button
                    type="button"
                    onclick={nextImage}
                    aria-label="Next image"
                    class="absolute right-2 sm:-right-12 top-1/2 -translate-y-1/2 p-3 rounded-full bg-slate-900/90 text-cyan-300 hover:bg-cyan-500 hover:text-slate-950 transition-colors border border-cyan-500/30"
                >
                    <CaretRightOutline class="w-6 h-6" />
                </button>
            {/if}

            <!-- Caption -->
            {#if activeImage?.alt}
                <p
                    class="mt-4 text-sm text-slate-300 font-mono text-center bg-slate-900/80 px-4 py-2 rounded-xl border border-white/10 max-w-2xl"
                >
                    {activeImage.alt}
                </p>
            {/if}
        </div>
    </div>
{/if}
