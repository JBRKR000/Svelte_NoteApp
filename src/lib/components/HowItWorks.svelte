<script lang="ts">
    import { fade, fly } from 'svelte/transition';
    import { onMount } from 'svelte';

    let sectionRef: HTMLElement;
    export let animationFinished = false;
    let isVisible = false;

    function handleIntersection(entries: IntersectionObserverEntry[]) {
        if (entries[0].isIntersecting) {
            isVisible = true;
        }
    }

    onMount(() => {
        const observer = new IntersectionObserver(handleIntersection, { threshold: 0.2 });
        if (sectionRef) observer.observe(sectionRef);
        return () => observer.disconnect();
    });
</script>

<section
    id="howItWorks"
    bind:this={sectionRef}
    class="font-manrope flex flex-col items-center justify-center px-4 py-16 pt-96 pb-96 text-white"
>
    <h2 class="mb-10 text-center text-4xl font-bold md:text-5xl">How It Works</h2>

    {#if animationFinished || isVisible}
        <div class="grid w-full max-w-6xl grid-cols-1 gap-8 md:grid-cols-3">
            <!-- BOX 1 -->
            <div
                class="relative group rounded-xl p-[2px] bg-gradient-to-r from-indigo-500 via-pink-500 to-cyan-400 bg-[length:300%_300%] animate-gradient"
                in:fly={{ x: -100, duration: 600, delay: 500 }}
            >
                <div class="relative z-10 h-full w-full rounded-xl bg-[#0f0f0f] p-6 text-center">
                    <svg
                        class="mb-4 h-12 w-12 text-cyan-400 transition-transform duration-500 group-hover:scale-125 group-hover:-rotate-12 group-hover:text-pink-400"
                        fill="none"
                        stroke="currentColor"
                        stroke-width="2"
                        viewBox="0 0 24 24"
                    >
                        <path
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            d="M16.862 3.487a2.25 2.25 0 1 1 3.182 3.182L7.5 19.213l-4 1 1-4 14.362-14.726z"
                        />
                    </svg>
                    <h3 class="mb-2 text-xl font-semibold">Create Notes</h3>
                    <p class="text-gray-300">
                        Quickly add your thoughts, tasks, or ideas in a simple and intuitive editor.
                    </p>
                </div>
            </div>

            <!-- BOX 2 -->
            <div
                class="relative group rounded-xl p-[2px] bg-gradient-to-r from-indigo-500 via-pink-500 to-cyan-400 bg-[length:300%_300%] animate-gradient"
                in:fade={{ duration: 600, delay: 500 }}
            >
                <div class="relative z-10 h-full w-full rounded-xl bg-[#0f0f0f] p-6 text-center">
                    <svg
                        class="mb-4 h-12 w-12 text-emerald-400 transition-transform duration-500 group-hover:animate-pulse"
                        fill="none"
                        stroke="currentColor"
                        stroke-width="2"
                        viewBox="0 0 24 24"
                    >
                        <path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h7" />
                    </svg>
                    <h3 class="mb-2 text-xl font-semibold">Organize</h3>
                    <p class="text-gray-300">
                        Keep your notes organized and accessible from anywhere, anytime.
                    </p>
                </div>
            </div>

            <!-- BOX 3 -->
            <div
                class="relative group rounded-xl p-[2px] bg-gradient-to-r from-indigo-500 via-pink-500 to-cyan-400 bg-[length:300%_300%] animate-gradient"
                in:fly={{ x: 100, duration: 600, delay: 500 }}
            >
                <div class="relative z-10 h-full w-full rounded-xl bg-[#0f0f0f] p-6 text-center">
                    <svg
                        class="mb-4 h-12 w-12 text-pink-400 transition-transform duration-500 group-hover:animate-bounce"
                        fill="none"
                        stroke="currentColor"
                        stroke-width="2"
                        viewBox="0 0 24 24"
                    >
                        <path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" />
                    </svg>
                    <h3 class="mb-2 text-xl font-semibold">Be Productive</h3>
                    <p class="text-gray-300">
                        Focus on what matters and boost your productivity every day.
                    </p>
                </div>
            </div>
        </div>
    {/if}
</section>

<style>
.animate-gradient {
    background-size: 300% 300%;
    animation: gradientMove 4s ease-in-out infinite;
}

@keyframes gradientMove {
    0% {
        background-position: 0% 50%;
    }
    50% {
        background-position: 100% 50%;
    }
    100% {
        background-position: 0% 50%;
    }
}
</style>