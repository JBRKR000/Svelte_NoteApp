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
	let caretInterval: ReturnType<typeof setInterval>;

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

		caretInterval = setInterval(() => {
			if (!typeFinished) showCaret = !showCaret;
		}, 500);
	});

	onDestroy(() => {
		clearInterval(caretInterval);
	});
</script>

<div
	class="presentation font-manrope flex flex-col min-h-screen items-center justify-center"
>
	<div>
		<h1 class="text-3xl font-bold whitespace-pre-line text-white md:text-5xl">
			{displayed}<span class="carret text-white">{!typeFinished && showCaret ? '|' : ''}</span>
		</h1>
	</div>

    <div class="mt-4 text-white md:text-2xl">
        {#if typeFinished}
    <button
        class="px-6 py-2 font-manrope rounded-2xl border-2 border-transparent hover:opacity-50 duration-500 text-white relative overflow-hidden"
        style="background: linear-gradient(to right, #312e81, #000) padding-box, linear-gradient(90deg, #6366f1, #06b6d4) border-box; background-clip: padding-box, border-box;"
        transition:fade
    >
        Discover how it works
    </button>
{/if}
    </div>
</div>
