<script lang="ts">
    import { duration } from 'drizzle-orm/gel-core';
    import { onMount, tick, onDestroy } from 'svelte';
    import {fade} from 'svelte/transition';
    import HowItWorks from './HowItWorks.svelte';
    let displayed = '';
    let text = 'Start being productive today.';
    let delay = 75;
    let typeFinished = false;
    let showCaret = true;
    let splashVisible = false;
    let caretInterval: ReturnType<typeof setInterval>;
    export let animationFinished = false;
    let offsetX = 0;
    let offsetY = 0;
    function handleMouseMove(event: MouseEvent) {
        const centerX = window.innerWidth / 2;
        const centerY = window.innerHeight / 2;
        offsetX = ((event.clientX - centerX) / centerX) * 5;
        offsetY = ((event.clientY - centerY) / centerY) * 5;
    }

    function smoothScrollTo(element: HTMLElement, duration = 1200, onDone?: () => void) {
        const start = window.scrollY;
        const end = element.getBoundingClientRect().bottom + window.scrollY;
        const change = end - start;
        const startTime = performance.now();

        function animateScroll(currentTime: number) {
            const elapsed = currentTime - startTime;
            const progress = Math.min(elapsed / duration, 1);
            window.scrollTo(0, start + change * progress);
            if (progress < 1) {
                requestAnimationFrame(animateScroll);
            } else if (onDone) {
                onDone();
            }
        }
        requestAnimationFrame(animateScroll);
    }

    function typeText() {
        for (let i = 0; i < text.length; i++) {
            setTimeout(async () => {
                displayed += text[i];
                if (i === text.length - 1) {
                    typeFinished = true;
                    clearInterval(caretInterval);
                    showCaret = false;
                    await tick();
                }
            }, i * delay);
        }
    }

    onMount(() => {
        typeText();
        splashVisible = true;
        caretInterval = setInterval(() => {
            if (!typeFinished) showCaret = !showCaret;
        }, 500);
    });

    onDestroy(() => {
        clearInterval(caretInterval);
    });
</script>

<svelte:window on:mousemove={handleMouseMove} />

<div
    class="presentation font-manrope flex flex-col pt-96 pb-96 items-center justify-center relative min-h-screen"
>
    {#if splashVisible}
    <img
        src="/splash.png"
        alt="Splash"
        class="pointer-events-none select-none"
        style="
            position: absolute;
            left: 50%;
            top: 45%;
            transform: translate(-50%, -50%) translate({offsetX}px, {offsetY}px);
            width: 600px;
            max-width: 80vw;
            opacity: 0.5;
            z-index: 1;
        "
        transition:fade={{ duration: 500, delay: 250 }}
    />
    {/if}
    <div style="position: relative; z-index: 2;">
        <h1 class="text-3xl font-bold whitespace-pre-line text-white md:text-5xl">
            {displayed}<span class="carret text-white">{!typeFinished && showCaret ? '|' : ''}</span>
        </h1>
    </div>

    <div class="mt-4 text-white md:text-2xl" style="position: relative; z-index: 2;">
        {#if typeFinished}
    <button
        class="px-6 py-2 font-manrope rounded-2xl border-2 border-transparent hover:opacity-50 duration-500 text-white relative overflow-hidden"
        style="background: linear-gradient(to right, #312e81, #000) padding-box, linear-gradient(90deg, #6366f1, #06b6d4) border-box; background-clip: padding-box, border-box;"
        transition:fade
        onclick={() => {
            const section = document.getElementById('howItWorks');
            if (section) {
                smoothScrollTo(section, 1200, () => {
                   animationFinished = true;
                });
            }
        }}
    >
        Discover how it works
    </button>
{/if}
    </div>
</div>